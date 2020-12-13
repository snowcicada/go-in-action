## 死锁
Go语言在运行时能够检测一些死锁，但是这对于防止死锁并没有太多的帮助。

## 执行结果
```text
fatal error: all goroutines are asleep - deadlock!

goroutine 1 [semacquire]:
sync.runtime_Semacquire(0xc000016078)
	/usr/local/go/src/runtime/sema.go:56 +0x45
sync.(*WaitGroup).Wait(0xc000016070)
	/usr/local/go/src/sync/waitgroup.go:130 +0x65
main.main()
	/Users/snowcicada/code/go-in-action/src/001deadlock/001deadlock.go:36 +0x127

goroutine 6 [semacquire]:
sync.runtime_SemacquireMutex(0xc000016094, 0x10d5d00, 0x1)
	/usr/local/go/src/runtime/sema.go:71 +0x47
sync.(*Mutex).lockSlow(0xc000016090)
	/usr/local/go/src/sync/mutex.go:138 +0x105
sync.(*Mutex).Lock(...)
	/usr/local/go/src/sync/mutex.go:81
main.main.func1(0xc000016080, 0xc000016090)
	/Users/snowcicada/code/go-in-action/src/001deadlock/001deadlock.go:26 +0x1be
created by main.main
	/Users/snowcicada/code/go-in-action/src/001deadlock/001deadlock.go:34 +0xef

goroutine 7 [semacquire]:
sync.runtime_SemacquireMutex(0xc000016084, 0x10d5d00, 0x1)
	/usr/local/go/src/runtime/sema.go:71 +0x47
sync.(*Mutex).lockSlow(0xc000016080)
	/usr/local/go/src/sync/mutex.go:138 +0x105
sync.(*Mutex).Lock(...)
	/usr/local/go/src/sync/mutex.go:81
main.main.func1(0xc000016090, 0xc000016080)
	/Users/snowcicada/code/go-in-action/src/001deadlock/001deadlock.go:26 +0x1be
created by main.main
	/Users/snowcicada/code/go-in-action/src/001deadlock/001deadlock.go:35 +0x119
```