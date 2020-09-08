---
title: How to increase timeout for debug?
categories: gui-basis
author: Vasiliy Kharitonov
systems:
  SAP EWM 9.4
  SAP S/4HANA
---

It is might be quite annoying to receive timeout after going deep into a debug session. Fortunately, there is a way to extend timeout for debug.

You can temporary change timeout for debug using transaction **RZ11** for changing profile parameters dynamically. Please consider first some important points:

- Changing Profile parameter in RZ11 will influence everyone working on the same application server. E.g. if you extend maximum debug time indefinetly, no one will receive timeouts for debug, which might have an influence on system performance.
- RZ11 is nice for temporary changes. It changes parameters dynamically, meaning it changes the current value, but doesn't override a default one. Practically it means, that after application server restart all changes done with RZ11 will be lost.

You can perform the following actions to increase timeout for debug:
1. Open transaction **RZ11**.
2. Provide parameter name `rdisp/max_debug_lazy_time` and press *Display*.
3. In the section *Value of Profile Parameter `rdisp/max_debug_lazy_time`* you will see both current and default values for timeout for debug in seconds. Usually it is `600` seconds meaning 10 minutes.
4. Press button *Change Value (Ctrl+F5)*, fill new value in seconds (or provide `0` for no timeout at all), press *Save change (Ctrl+S)*.
5. Thats it. For the new timeout value to work for your user you need to relogin to the system.
