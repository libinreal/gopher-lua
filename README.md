
===============================================================================
GopherLua: VM and compiler for Lua in Go.
===============================================================================

.. image:: https://godoc.org/github.com/yuin/gopher-lua?status.svg
    :target: http://godoc.org/github.com/yuin/gopher-lua

.. image:: https://travis-ci.org/yuin/gopher-lua.svg
    :target: https://travis-ci.org/yuin/gopher-lua

.. image:: https://coveralls.io/repos/yuin/gopher-lua/badge.svg
    :target: https://coveralls.io/r/yuin/gopher-lua

.. image:: https://badges.gitter.im/Join%20Chat.svg
    :alt: Join the chat at https://gitter.im/yuin/gopher-lua
    :target: https://gitter.im/yuin/gopher-lua?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge

|
----------------------------------------------------------------
License
----------------------------------------------------------------
MIT

----------------------------------------------------------------
Author
----------------------------------------------------------------
Yusuke Inuzuka

# 更新日志

### version 0.0.1
* 2022-09-22 修改了 ``github.com/yuin/gopher-lua/auxlib.go`` 的 `CheckString()` 方法
```
    func (ls *LState) CheckString(n int) string {
        v := ls.Get(n)
        if lv, ok := v.(LString); ok {
            return string(lv)
        } else if LVCanConvToString(v) {
            return ls.ToString(n)
        }
        // 2022-09-22 allow param absence
        // ls.TypeError(n, LTString)
        return ""
    }
```
