---
title: "C_sharp_string2class"
date: 2022-05-25T13:49:37Z
draft: false
---

## String to Class and then call Method

```C#
    var t = Type.GetType("WebApplication1.Services."+ServiceName+", WebApplication1");
    
    var service_instance = Activator.CreateInstance((t));
    ServiceValues actual = (ServiceValues)service_instance.GetType().GetMethod(FunctionName).Invoke(service_instance, new object[] { temp, fm_repo }); 
```

第一行可以參考後，再進一步優化程式。
```C#
    Console.WriteLine(typeof(TService).AssemblyQualifiedName);
```

有考慮進一步改寫為 function，參數可能是 `className`, `methodName`, 參數：`new object[] { temp, fm_repo }`