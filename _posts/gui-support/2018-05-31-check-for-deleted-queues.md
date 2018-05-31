---
title: How to check for deleted qRFC queues?
author: Vasiliy Kharitonov
categories: gui-support
systems:
- SAP EWM 9.4
---

Deletion of queues from SMQ1 and SMQ2 is usually a bad idea. We advice not to do it unless you are completely sure what you are doing and what consequences will occur. If something was deleted, it is usually impossible to recover the data. Remember, if you aren't completely sure what to do with some inbound queue with an error, you can save it to SMQ3 (right click - Save to SMQ3).

If you suspects, that something was deleted, you can check with transaction SM21 (system log). Message IDs for deletion are `Q2` or `Q2*` (i.e. `Q26`), depending on the case.

Keep in mind, that system log has a certain lifetime, so you won't see messages there for a long time ago.
