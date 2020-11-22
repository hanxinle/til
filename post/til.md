#ifndef XTHREAD_POOL_H
#define XTHREAD_POOL_H

#ifdef _WIN32
#ifdef XCOM_EXPORTS
#define XCOM_API __declspec(dllexport)
#else
#define XCOM_API __declspec(dllimport)
#endif
#else
#define XCOM_API
#endif
#include <vector>
class XThread;
class XTask;
class XCOM_API XThreadPool
{
public:
    ///////////////////////////////////////////////////////////////////////////
    /// @brief 鑾峰彇XThreadPool鐨勯潤鎬佸璞� 锛堥潤鎬佸嚱鏁帮級
    /// @return XThreadPool 闈欐€佸璞＄殑鎸囬拡
    ///////////////////////////////////////////////////////////////////////////
	static XThreadPool* Get()
	{
		static XThreadPool p;
		return &p;
	}
    ///////////////////////////////////////////////////////////////////////////
    /// @brief 鍒濆鍖栨墍鏈夌嚎绋嬪苟鍚姩绾跨▼锛屽垱寤哄彿event_base ,骞跺湪绾跨▼涓紑濮嬫帴鏀舵秷鎭�
	void Init(int thread_count);

    ///////////////////////////////////////////////////////////////////////////
    /// @brief 鍒嗗彂浠诲姟鍒扮嚎绋嬩腑鎵ц锛屼細璋冪敤task鐨処nit杩涜浠诲姟鍒濆鍖�
    ///        浠诲姟浼氳疆璇㈠垎鍙戝埌绾跨▼姹犱腑鐨勫悇涓嚎绋�
    /// @param task 浠诲姟鎺ュ彛瀵硅薄锛孹Task闇€瑕佺敤鎴疯嚜宸辩户鎵垮苟閲嶈浇Init鍑芥暟
	void Dispatch(XTask *task);

    XThreadPool() {};
private:
	///绾跨▼鏁伴噺
	int thread_count_ = 0;

    ///涓婁竴娆″垎鍙戝緱鍒扮嚎绋嬶紝鐢ㄤ簬杞
	int last_thread_ = -1;

	///绋嬫睜绾跨▼闃熷垪
	std::vector<XThread *>threads_;
	

};

#endif}
//锟竭程硷拷锟斤拷
void XThread::Activate()
{
#ifdef _WIN32
	int re = send(this->notify_send_fd_, "c", 1, 0);
#else
	int re = write(this->notify_send_fd_, "c", 1);
#endif
	if (re <= 0)
	{
		cerr << "XThread::Activate() failed!" << endl;
	}
}
//锟斤拷锟斤拷锟竭筹拷
void XThread::Start()
{
	Setup();
	//锟斤拷锟斤拷锟竭筹拷
	thread th(&XThread::Main,this);

	//锟较匡拷锟斤拷锟斤拷锟竭筹拷锟斤拷系
	th.detach();
}
//锟斤拷装锟竭程ｏ拷锟斤拷始锟斤拷event_base锟酵管碉拷锟斤拷锟斤拷锟铰硷拷锟斤拷锟节硷拷锟斤拷
bool XThread::Setup()
{
	//windows锟斤拷锟斤拷锟絪ocket linux锟矫管碉拷
#ifdef _WIN32
	//锟斤拷锟斤拷一锟斤拷socketpair 锟斤拷锟皆伙拷锟斤拷通锟斤拷 fds[0] 锟斤拷 fds[1]写 
	evutil_socket_t fds[2];
	if (evutil_socketpair(AF_INET, SOCK_STREAM, 0, fds) < 0)
	{
		cout << "evutil_socketpair failed!" << endl;
		return false;
	}
	//锟斤拷锟矫成凤拷锟斤拷锟斤拷
	evutil_make_socket_nonblocking(fds[0]);
	evutil_make_socket_nonblocking(fds[1]);
#else
	//锟斤拷锟斤拷锟侥管碉拷 锟斤拷锟斤拷锟斤拷send recv锟斤拷取 read write
	int fds[2];
	if (pipe(fds))
	{
		cerr << "pipe failed!" << endl;
		return false;
	}
#endif

	//锟斤拷取锟襟定碉拷event锟铰硷拷锟叫ｏ拷写锟斤拷要锟斤拷锟斤拷
	notify_send_fd_ = fds[1];

	//锟斤拷锟斤拷libevent锟斤拷锟斤拷锟侥ｏ拷锟斤拷锟斤拷锟斤拷
	event_config *ev_conf = event_config_new();
	event_config_set_flag(ev_conf, EVENT_BASE_FLAG_NOLOCK);
	this->base_ = event_base_new_with_config(ev_conf);
	event_config_free(ev_conf);
	if (!base_)
	{
		cerr << "event_base_new_with_config failed in thread!" << endl;
		return false;
	}

	//锟斤拷锟接管碉拷锟斤拷锟斤拷锟铰硷拷锟斤拷锟斤拷锟节硷拷锟斤拷锟竭筹拷执锟斤拷锟斤拷锟斤拷
	event *ev = event_new(base_, fds[0], EV_READ | EV_PERSIST, NotifyCB, this);
	event_add(ev, 0);

	return true;
}
//锟竭筹拷锟斤拷诤锟斤拷锟�
void XThread::Main()
{
	cout << id << " XThread::Main() begin" << endl;
    if (!base_)
    {
        cerr << "XThread::Main faield! base_ is null " << endl;
        cerr << "In windows set WSAStartup(MAKEWORD(2, 2), &wsa)" << endl;
        return;
    }
	event_base_dispatch(base_);
	event_base_free(base_);

	cout << id << " XThread::Main() end" << endl;
}


XThread::XThread()
{
}


XThread::~XThread()
{
}
