---
title: "歷程偵錯 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# 歷程偵錯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

歷程偵錯是取決於 IntelliTrace 所收集資訊的偵錯模式。  它可讓您向後和向前逐步執行您的應用程式，並檢查其狀態。  
  
 您可以在 Visual Studio Enterprise 版本 \(而非 Professional 或 Community 版本\) 中使用 IntelliTrace。  
  
## 為何使用歷程偵錯？  
 設定中斷點來找出 Bug 可能相當容易出錯。  您可以在接近程式碼中懷疑為 Bug 所在的位置設定中斷點，然後在偵錯工具中執行應用程式，並希望您的中斷點找到錯誤位置，以及執行中斷可能會顯示 Bug 來源的位置。  否則，您必須嘗試在程式碼的某一處設定中斷點，然後重新執行偵錯工具，以重複執行測試步驟，直到找出問題。  
  
 ![設定中斷點](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 您可以使用 IntelliTrace 和歷程偵錯來漫遊應用程式，並檢查其狀態 \(呼叫堆疊和區域變數\)，而不需要設定中斷點、重新啟動偵錯，以及重複測試步驟。  這可以節省許多時間，特別是當 Bug 位於測試案例的較深處而需要花很長的時間執行時。  
  
## 如何開始使用歷程偵錯？  
 預設會開啟 IntelliTrace。  您只需要決定感興趣的事件和函式呼叫。  如需定義您想要尋找之項目的詳細資訊，請參閱 [IntelliTrace 功能](../debugger/intellitrace-features.md)。  如需使用 IntelliTrace 偵錯的逐步帳戶，請參閱[逐步解說：使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)。  
  
## 使用歷程偵錯巡覽程式碼  
 讓我們從內含 Bug 的簡單程式開始。  在 C\# 主控台應用程式中，加入下列程式碼：  
  
```c#  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 我們假設呼叫 `AddAll()` 之後的 `resultInt` 預期值是 20 \(遞增 `testInt` 20 次的結果\)。  \(我們也假設您看不到 `AddInt()` 中的 Bug\)。但是，結果實際上是 44。  如何在不逐步執行 `AddAll()` 10 次的情況下找到 Bug？  我們可以使用歷程偵錯更迅速且更輕鬆地找到 Bug。  方式如下：  
  
1.  在 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] \/ \[一般\] 中，確定已啟用 IntelliTrace，然後選取 \[IntelliTrace 事件和呼叫資訊\] 選項。  如果您未選取此選項，則無法看到巡覽邊 \(如下所述\)。  
  
2.  在 `Console.WriteLine(resultInt);` 行上設定中斷點。  
  
3.  開始偵錯。  程式碼會執行到中斷點。  在 \[區域變數\] 視窗中，您可以看到 `resultInt` 的值是 44。  
  
4.  開啟 \[診斷工具\] 視窗 \(\[偵錯\] \/ \[顯示診斷工具\]\)。  程式碼視窗應該如下所示：  
  
     ![中斷點上的程式碼視窗](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  您應該會在左邊界旁邊看到雙箭頭，就在中斷點正上方。  這個區域稱為巡覽邊，並用於歷程偵錯。  按一下箭頭。  
  
     在程式碼視窗中，您應該會看到前一行程式碼 \(`int resultInt = AddIterative(testInt);`\) 加上粉紅色。  在視窗上方，您應該會看到一則訊息，指出現在您正在使用歷程偵錯。  
  
     程式碼視窗現在如下所示：  
  
     ![歷程偵錯模式中的程式碼視窗](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  現在您可以逐步執行 `AddAll()` 方法 \(**F11**，或巡覽邊中的 \[逐步執行\] 按鈕\)。  逐步往前執行 \(**F10**，或巡覽邊中的 \[移至下一個呼叫\]\)。  粉紅色行現在位於 `j = AddInt(j);` 行。  在此情況下，**F10** 不會逐步執行下一行程式碼。  而是會逐步執行至下一個函式呼叫。  歷程偵錯呼叫會巡覽不同的呼叫，並略過不包括函式呼叫的程式碼行。  
  
7.  現在會逐步執行 `AddInt()` 方法。  您應該會立即看到此程式碼中的 Bug。  
  
 此程序只會大略探討您如何使用歷程偵錯。  若要深入了解不同的設定以及巡覽邊中不同按鈕的效果，請參閱 [IntelliTrace 功能](../debugger/intellitrace-features.md)。