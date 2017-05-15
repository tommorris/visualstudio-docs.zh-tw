---
title: "註釋函式參數和傳回值 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Outptr_opt_result_bytebuffer_to_"
  - "_Inout_updates_all_opt_"
  - "_Post_equal_to_"
  - "_Outptr_opt_result_maybenull_"
  - "_Out_writes_bytes_all_"
  - "_Out_writes_all_opt_"
  - "_In_opt_"
  - "_Outptr_"
  - "_Outptr_result_maybenull_"
  - "_Outref_result_bytebuffer_all_maybenull_"
  - "_Inout_updates_opt_z_"
  - "_Inout_updates_z_"
  - "_Out_writes_"
  - "_Out_writes_to_ptr_opt_z_"
  - "_In_reads_to_ptr_opt_"
  - "_Ret_writes_to_maybenull_"
  - "_Outref_result_maybenull_"
  - "_Ret_writes_bytes_"
  - "_Outptr_result_bytebuffer_"
  - "_Out_writes_opt_"
  - "_Inout_updates_bytes_opt_"
  - "_In_z_"
  - "_Inout_updates_to_"
  - "_Ret_maybenull_"
  - "_Ret_writes_bytes_to_"
  - "_Ret_z_"
  - "_COM_Outptr_"
  - "_Ret_maybenull_z_"
  - "_Out_opt_"
  - "_In_reads_opt_z_"
  - "_Outptr_result_bytebuffer_to_"
  - "_Ret_notnull_"
  - "_COM_Outptr_opt_result_maybenull_"
  - "_Inout_updates_to_opt_"
  - "_Inout_updates_"
  - "_Outptr_opt_result_buffer_"
  - "_Outptr_result_buffer_to_"
  - "_Out_writes_to_ptr_opt_"
  - "_Out_writes_bytes_all_opt_"
  - "_Inout_updates_all_"
  - "_Deref_inout_range_"
  - "_Ret_writes_"
  - "_Out_writes_z_"
  - "_Ret_writes_to_"
  - "_Out_writes_to_ptr_z_"
  - "_Out_writes_bytes_to_opt_"
  - "_In_reads_or_z_"
  - "_Inout_updates_bytes_to_"
  - "_In_reads_z_"
  - "_In_opt_z_"
  - "_Outref_result_buffer_maybenull_"
  - "_Ret_range_"
  - "_COM_Outptr_opt_"
  - "_Ouptr_opt_result_maybenull_z_"
  - "_In_reads_opt_"
  - "_Inout_"
  - "_Field_range_"
  - "_Ret_writes_z_"
  - "_Out_writes_to_"
  - "_Out_writes_to_ptr_"
  - "_Inout_opt_z_"
  - "_Outref_"
  - "_Deref_out_range_"
  - "_Outref_result_buffer_"
  - "_Outref_result_buffer_to_"
  - "_Outref_result_bytebuffer_to_maybenull_"
  - "_In_reads_bytes_"
  - "_Outptr_opt_result_buffer_to_"
  - "_Outref_result_buffer_all_"
  - "_Out_writes_bytes_to_"
  - "_Result_zeroonfailure_"
  - "_In_reads_bytes_opt_"
  - "_Outref_result_buffer_to_maybenull_"
  - "_Outref_result_bytebuffer_all_"
  - "_Outref_result_buffer_all_maybenull_"
  - "_Ret_writes_maybenull_z_"
  - "_In_range_"
  - "_Inout_updates_bytes_all_opt_"
  - "_Outref_result_bytebuffer_to_"
  - "_Inout_updates_bytes_to_opt_"
  - "_Pre_equal_to_"
  - "_Ret_writes_bytes_maybenull_"
  - "_COM_Outptr_result_maybenull_"
  - "_Ret_writes_maybenull_"
  - "_Out_writes_bytes_"
  - "_Outptr_opt_"
  - "_Out_writes_opt_z_"
  - "_Outref_result_nullonfailure_"
  - "_Outptr_opt_result_z_"
  - "_Inout_opt_"
  - "_Deref_in_range_"
  - "_Outptr_result_z_"
  - "_In_reads_to_ptr_opt_z_"
  - "_Struct_size_bytes_"
  - "_Outptr_result_nullonfailure_"
  - "_In_"
  - "_Inout_updates_bytes_"
  - "_In_reads_to_ptr_z_"
  - "_Ret_writes_bytes_to_maybenull"
  - "_Outptr_opt_result_nullonfailure_"
  - "_In_reads_to_ptr_"
  - "_Outptr_result_buffer_"
  - "_Out_"
  - "_Outref_result_bytebuffer_maybenull_"
  - "_Outptr_result_maybenull_z_"
  - "_In_reads_"
  - "_Inout_updates_opt_"
  - "_Out_writes_to_opt_"
  - "_Outptr_opt_result_bytebuffer_"
  - "_Out_writes_all_"
  - "_Out_range_"
  - "_Inout_updates_bytes_all_"
  - "_Inout_z_"
  - "_Outref_result_bytebuffer_"
  - "_Result_nullonfailure_"
  - "_Ret_null_"
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 註釋函式參數和傳回值
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這篇文章描述的註解為簡單的函式參數的一般用法，純量和結構和類別的指標，和大部分的緩衝區類型。  本文也會顯示註釋的常見使用模式。 函式相關的其他註解，請參閱 [註釋函式行為](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>指標參數  
 下表中之附註，指標參數的註解，當分析器] 中報告的錯誤如果指標是 null。  這適用於指標，並指向任何資料項目。  
  
 **註解和描述**  
  
-   `_In_`  
  
     輸入的參數是純量、 結構、 結構的指標和類似加上附註。  明確可根據簡單的純量。  參數必須是有效前的狀態，而且不會被修改。  
  
-   `_Out_`  
  
     加上附註是純量、 結構、 結構的指標和類似的輸出參數。  不會套用這無法傳回值的物件 — 例如，純量的傳值方式傳遞。  參數不一定要有效前的狀態，但必須是有效後的狀態。  
  
-   `_Inout_`  
  
     加上附註函式所變更的參數。  它必須是在前的狀態和後置狀態下，有效，但假設有不同的值之前和之後呼叫。 必須套用至可修改的值。  
  
-   `_In_z_`  
  
     做為輸入的 null 終止字串指標。  在前的狀態，字串必須是有效的。  變化 `PSTR`, ，其中已經具有正確的註解、 慣用發佈點。  
  
-   `_Inout_z_`  
  
     將修改 null 結束的字元陣列的指標。  它必須是有效之前和之後呼叫，但值假設為已變更。  可能會移動 null 結束字元，但可能會存取到原始的 null 結束字元的元素。  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     陣列，可讀取之函式指標。  陣列的大小是 `s` 項目，其中都必須有效。  
  
      `_bytes_` 變異提供大小，以位元組為單位，而不是項目。 只有當大小不能表示為項目時，請使用此選項。  例如， `char` 字串會使用 `_bytes_` 變異類似函式時，才會使用 `wchar_t` 會。  
  
-   `_In_reads_z_(s)`  
  
     陣列是以 null 結束，且具有已知的大小指標。 最多 null 結束字元的項目 — 或 `s` 如果沒有 null 結束字元，必須是有效前的狀態。  如果已知大小 （位元組），調整 `s` 項目大小。  
  
-   `_In_reads_or_z_(s)`  
  
     是以 null 結束，或具有已知的大小，或兩者的陣列指標。 最多 null 結束字元的項目 — 或 `s` 如果沒有 null 結束字元，必須是有效前的狀態。  如果已知大小 （位元組），調整 `s` 項目大小。  (用於 `strn` 系列。)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     陣列的指標 `s` 項目 （分別 位元組為單位），將會寫入由函式。  陣列元素並沒有在前置狀態下，會有效，且未指定後的狀態中的有效項目數目。  如果參數型別上的註解，會套用在後的狀態。 例如，試想下列程式碼。  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     在此範例中，呼叫端提供的緩衝區 `size` 項目 `p1`。  `MyStringCopy` 讓某些這些項目是有效的。 更重要的是， `_Null_terminated_` 上的註解 `PWSTR` 表示 `p1` 後的狀態是以 null 結束。  如此一來，有效的項目數目仍完整定義，但不需要特定的項目計數。  
  
      `_bytes_` 變異提供大小，以位元組為單位，而不是項目。 只有當大小不能表示為項目時，請使用此選項。  例如， `char` 字串會使用 `_bytes_` 變異類似函式時，才會使用 `wchar_t` 會。  
  
-   `_Out_writes_z_(s)`  
  
     陣列的指標 `s` 項目。  項目並沒有為有效前的狀態。  在後置狀態下，設定項目，透過 null 結束字元，必須存在，必須是有效的。  如果已知大小 （位元組），調整 `s` 項目大小。  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     陣列，它會讀取和寫入至函式的指標。  它的大小是 `s` 項目，且在前的狀態和狀態後有效。  
  
      `_bytes_` 變異提供大小，以位元組為單位，而不是項目。 只有當大小不能表示為項目時，請使用此選項。  例如， `char` 字串會使用 `_bytes_` 變異類似函式時，才會使用 `wchar_t` 會。  
  
-   `_Inout_updates_z_(s)`  
  
     陣列是以 null 結束，且具有已知的大小指標。 設定項目，透過 null 結束字元 — 必須存在，必須是有效的前的狀態和後置狀態。  後置狀態中的值會假設不同於前的狀態; 中的值這包括 null 結束字元的位置。 如果已知大小 （位元組），調整 `s` 項目大小。  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     陣列的指標 `s` 項目。  項目並沒有為有效前的狀態。  在後置狀態下，最多的項目 `c`第個項目必須是有效。  如果已知大小 （位元組），調整 `s` 和 `c` 所使用的項目大小 `_bytes_` 變體，其定義如下︰  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     換句話說，每個項目存在於緩衝區中最多 `s` 前的狀態處於有效後的狀態。  例如:   
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     陣列，它是讀取 / 寫入函式指標。  它的大小是 `s` 項目，其中都必須是有效前的狀態、 和 `c` 項目後的狀態必須是有效。  
  
      `_bytes_` 變異提供大小，以位元組為單位，而不是項目。 只有當大小不能表示為項目時，請使用此選項。  例如， `char` 字串會使用 `_bytes_` 變異類似函式時，才會使用 `wchar_t` 會。  
  
-   `_Inout_updates_z_(s)`  
  
     陣列是以 null 結束，且具有已知的大小指標。 設定項目，透過 null 結束字元 — 必須存在，必須是有效的前的狀態和後置狀態。  後置狀態中的值會假設不同於前的狀態; 中的值這包括 null 結束字元的位置。 如果已知大小 （位元組），調整 `s` 項目大小。  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     陣列的指標 `s` 項目。  項目並沒有為有效前的狀態。  在後置狀態下，最多的項目 `c`第個項目必須是有效。  如果已知大小 （位元組），調整 `s` 和 `c` 所使用的項目大小 `_bytes_` 變體，其定義如下︰  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     換句話說，每個項目存在於緩衝區中最多 `s` 前的狀態處於有效後的狀態。  例如:   
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     陣列，它是讀取 / 寫入函式指標。  它的大小是 `s` 項目，其中都必須是有效前的狀態、 和 `c` 項目後的狀態必須是有效。  
  
      `_bytes_` 變異提供大小，以位元組為單位，而不是項目。 只有當大小不能表示為項目時，請使用此選項。  例如， `char` 字串會使用 `_bytes_` 變異類似函式時，才會使用 `wchar_t` 會。  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     陣列，它是讀取 / 寫入大小的函式的指標 `s` 項目。 定義為等同於︰  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     換句話說，每個項目存在於緩衝區中最多 `s` 前的狀態無效前的狀態和後續狀態。  
  
      `_bytes_` 變異提供大小，以位元組為單位，而不是項目。 只有當大小不能表示為項目時，請使用此選項。  例如， `char` 字串會使用 `_bytes_` 變異類似函式時，才會使用 `wchar_t` 會。  
  
-   `_In_reads_to_ptr_(p)`  
  
     陣列的指標運算式 `p` – `_Curr_` (也就是 `p` 減 `_Curr_`) 由適當的語言和標準所定義。  之前的項目 `p` 前的狀態必須有效。  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Null 終端陣列的指標運算式 `p` – `_Curr_` (也就是 `p` 減 `_Curr_`) 由適當的語言和標準所定義。  之前的項目 `p` 前的狀態必須有效。  
  
-   `_Out_writes_to_ptr_(p)`  
  
     陣列的指標運算式 `p` – `_Curr_` (也就是 `p` 減 `_Curr_`) 由適當的語言和標準所定義。  之前的項目 `p` 沒有為有效前的狀態，而且必須是有效後的狀態。  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Null 終端陣列的指標運算式 `p` – `_Curr_` (也就是 `p` 減 `_Curr_`) 由適當的語言和標準所定義。  之前的項目 `p` 沒有為有效前的狀態，而且必須是有效後的狀態。  
  
## <a name="optional-pointer-parameters"></a>選擇性的指標參數  
 當指標的參數註釋包含 `_opt_`, ，它會指出參數可以是 null。 否則，註釋會執行不同版本不包含 `_opt_`。 以下是一份 `_opt_` 指標參數註釋的變數︰  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>輸出指標參數  
 輸出指標參數需要特殊的標記法來釐清 null 性質參數以及指向的位置上。  
  
 **註解和描述**  
  
-   `_Outptr_`  
  
     參數不可為 null，和在後的狀態，指向的位置不可以是 null 且必須是有效的。  
  
-   `_Outptr_opt_`  
  
     參數可以是 null，但後的狀態指向的位置不能是 null，而且必須是有效的。  
  
-   `_Outptr_result_maybenull_`  
  
     參數不可為 null，並後置狀態指向的位置可以是 null。  
  
-   `_Outptr_opt_result_maybenull_`  
  
     參數可以是 null，並後置狀態指向的位置可以是 null。  
  
 下表中其他的子字串會插入註釋名稱，來進一步限定註釋的意義。  不同的子字串 `_z`, ，`_COM_`, ，`_buffer_`, ，`_bytebuffer_`, ，和 `_to_`。  
  
> [!IMPORTANT]
>  如果 COM 註解的介面，使用這些註解的 COM 形式。 請勿與任何其他類型的介面使用的 COM 註解。  
  
 **註解和描述**  
  
-   `_Outptr_result_z_`  
  
     `_Outptr_opt_result_z_`  
  
     `_Outptr_result_maybenull_z_`  
  
     `_Ouptr_opt_result_maybenull_z_`  
  
     傳回的指標有 `_Null_terminated_` 註解。  
  
-   `_COM_Outptr_`  
  
     `_COM_Outptr_opt_`  
  
     `_COM_Outptr_result_maybenull_`  
  
     `_COM_Outptr_opt_result_maybenull_`  
  
     傳回的指標具有 COM 語意，而且因此帶有 `_On_failure_` 後置條件，傳回的指標是 null。  
  
-   `_Outptr_result_buffer_(s)`  
  
     `_Outptr_result_bytebuffer_(s)`  
  
     `_Outptr_opt_result_buffer_(s)`  
  
     `_Outptr_opt_result_bytebuffer_(s)`  
  
     傳回的指標會指向有效的緩衝區大小的 `s` 項目或位元組。  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     傳回的指標指向大小的緩衝區 `s` 項目或位元組，其中第一個 `c` 的有效值。  
  
 介面中的某些慣例假設為輸出參數會 nullified 失敗。  除了明確的 COM 程式碼下, 表中的表單是慣用的。  COM 程式碼，使用上一節中的所列的對應 COM 表單。  
  
 **註解和描述**  
  
-   `_Result_nullonfailure_`  
  
     修改其他註解。 結果是設定為 null，如果函式失敗。  
  
-   `_Result_zeroonfailure_`  
  
     修改其他註解。 在函數失敗時，結果是設定為零。  
  
-   `_Outptr_result_nullonfailure_`  
  
     傳回的指標會指向有效的緩衝區，如果函式成功，則為 null 函數失敗時。 此註解適用於非選擇性的參數。  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     傳回的指標會指向有效的緩衝區，如果函式成功，則為 null 函數失敗時。 此註解是選擇性參數。  
  
-   `_Outref_result_nullonfailure_`  
  
     傳回的指標會指向有效的緩衝區，如果函式成功，則為 null 函數失敗時。 此註解是做為參考參數。  
  
## <a name="output-reference-parameters"></a>輸出參考參數  
 參考參數的常見用法是輸出參數。  簡單輸出的參考參數，例如 `int&`—`_Out_` 提供正確的語意 （semantics）。  不過，當輸出值是指標，例如 `int *&`— 相等指標的註解喜歡 `_Outptr_ int **` 沒有提供正確的語意 （semantics）。  若要精確表示指標類型的輸出參考參數的語意，使用這些複合的註解︰  
  
 **註解和描述**  
  
-   `_Outref_`  
  
     結果必須是有效後的狀態，而且不能是 null。  
  
-   `_Outref_result_maybenull_`  
  
     結果必須在後置狀態下，有效，但可能是 null 後的狀態。  
  
-   `_Outref_result_buffer_(s)`  
  
     結果必須是有效後的狀態，而且不能是 null。 指向有效的緩衝區大小的 `s` 項目。  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     結果必須是有效後的狀態，而且不能是 null。 指向有效的緩衝區大小的 `s` 位元組。  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     結果必須是有效後的狀態，而且不能是 null。 指向的緩衝區 `s` 項目，其中第一個 `c` 的有效值。  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     結果必須是有效後的狀態，而且不能是 null。 指向的緩衝區 `s` 位元組，其中第一個 `c` 的有效值。  
  
-   `_Outref_result_buffer_all_(s)`  
  
     結果必須是有效後的狀態，而且不能是 null。 指向有效的緩衝區大小的 `s` 有效項目。  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     結果必須是有效後的狀態，而且不能是 null。 指向有效的緩衝區 `s` 位元組的有效項目。  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     結果必須在後置狀態下，有效，但可能是 null 後的狀態。 指向有效的緩衝區大小的 `s` 項目。  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     結果必須在後置狀態下，有效，但可能是 null 後的狀態。 指向有效的緩衝區大小的 `s` 位元組。  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     結果必須在後置狀態下，有效，但可能是 null 後的狀態。 指向的緩衝區 `s` 項目，其中第一個 `c` 的有效值。  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     結果必須在後置狀態下，有效，但可能是 null 在後置狀態。 指向的緩衝區 `s` 位元組，其中第一個 `c` 的有效值。  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     結果必須在後置狀態下，有效，但可能是 null 在後置狀態。 指向有效的緩衝區大小的 `s` 有效項目。  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     結果必須在後置狀態下，有效，但可能是 null 在後置狀態。 指向有效的緩衝區 `s` 位元組的有效項目。  
  
## <a name="return-values"></a>傳回值  
 函式的傳回值類似 `_Out_` 參數但位於不同的層級的 de-reference，而且您沒有考慮到結果指標的概念。  下列註釋，則傳回值是已標註的物件 — 純量、 結構的指標或緩衝區的指標。 這些註解有相同的語意對應 `_Out_` 註解。  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>其他常見的註解  
 **註解和描述**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     參數、 欄位或結果是在範圍中 （含） 從 `low` 到 `hi`。  相當於 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` 套用到適當的狀態前置或後置狀態條件以及標註的物件。  
  
    > [!IMPORTANT]
    >  雖然名稱可以包含 「 中 」 和 「 出 」 的語意 `_In_` 和 `_Out_` 執行 **不** 套用到這些註解。  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     註解的值就是 `expr`。  相當於 `_Satisfies_(_Curr_ == expr)` 套用到適當的狀態前置或後置狀態條件以及標註的物件。  
  
-   `_Struct_size_bytes_(size)`  
  
     套用至結構或類別宣告。  指出該類型的有效物件可能大於所宣告的類型，具有所指定的位元組數 `size`。  例如：  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     緩衝區大小，以位元組為單位的參數 `pM` 型別的 `MyStruct *` 再被視為︰  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>相關資源  
 [程式碼分析小組部落格](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>另請參閱  
 [使用 SAL 註釋減少 C/c + + 程式碼缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [了解 SAL](../code-quality/understanding-sal.md)   
 [註釋函式行為](../code-quality/annotating-function-behavior.md)   
 [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)   
 [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)   
 [指定套用註釋的時機和位置](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [內建函式](../code-quality/intrinsic-functions.md)   
 [最佳作法和範例](../code-quality/best-practices-and-examples-sal.md)