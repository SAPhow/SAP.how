---
title: How to monitor RFC integration?
categories: gui-support
systems:
- SAP EWM 9.4
---

All RFC messages with errors are saved in queues in transactions SMQ1 and SMQ2 for outbound and inbound messages correspondingly. There, messages with errors can be seen with status text and executed again manually. Also, LUW container can be seen there with all information to be sent.

Messages without errors are not shown in transactions above, but integration can be paused to see correct messages as well.

## How to stop RFC queue?

RFC queue can be paused via transactions SMQS and SMQR for outbound and inbound messages correspondingly. To stop the queue:

Select desired destination.
Press *Deregistration* and confirm.
Type for your destination will be changed from `R` to `U`. Recorded (stopped) messages can be executed manually via transactions SMQ1 and SMQ2.

Stopped destination can be started again by performing *Registration*.
