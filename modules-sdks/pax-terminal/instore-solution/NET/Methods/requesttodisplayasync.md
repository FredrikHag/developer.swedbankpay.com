---
title: RequestToDisplayAsync
description: Task\<NexoRequestResult\> RequestToDisplayAsync(string message)
---

Call RequestToDispalyAsync to display a message on the terminal. The method may only be called before or after a PaymentRequest has been sent to the terminal, which means it may be sent after a GetPaymentInstrument but not during the actual payment which in general starts when the amount is known. 
The displayed message stays until next request.

### Returns

A **NexoRequestResult**

```c#
public class NexoRequestResult
{
    public virtual string ResponseContent { get; set; }
    public NexoResponseResult ResponseResult { get; set; }
    public string ErrorCondition { get; set; }
    public string ResponseText { get; set; }
}
```
