---
title: "類別中的 let 繫結 (F#)"
description: "了解如何在類別定義中使用 'let' 繫結定義私用欄位和 F # 類別的私用函式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a>類別中的 let 繫結

您可以藉由定義私用欄位和 F # 類別的私用函式`let`類別定義中的繫結。


## <a name="syntax"></a>語法

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>備註
之後，類別標題和繼承的宣告，但任何成員定義之前，會顯示先前的語法。 語法是類似`let`外部類別，但類別中定義的名稱的繫結已限制為類別的範圍。 A`let`繫結會建立私用欄位或函式; 若要公開的資料或函式公開，宣告屬性或成員方法。

A`let`繫結，不是靜態的執行個體稱為`let`繫結。 執行個體`let`繫結執行時，會建立物件。 靜態`let`繫結是類別，可保證執行之前先使用該類型的靜態初始設定式的一部分。

執行個體中的程式碼`let`繫結可以使用主要建構函式參數。

上不允許屬性和存取範圍修飾詞`let`類別中的繫結。

下列程式碼範例將說明幾種類型的`let`類別中的繫結。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

輸出如下。

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>若要建立欄位的替代方式
您也可以使用`val`關鍵字建立私用欄位。 當使用`val`關鍵字，欄位未指定值時，該物件會建立，但改為使用預設值初始化。 如需詳細資訊，請參閱[明確欄位： val 關鍵字](explicit-fields-the-val-keyword.md)。

您也可以定義類別中的私用欄位，使用成員定義，並將關鍵字加入`private`的定義。 這很有用，如果您要變更成員的存取範圍，而不用重寫程式碼。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

## <a name="see-also"></a>另請參閱
[成員](index.md)

[類別中的 `do` 繫結](do-bindings-in-classes.md)

[`let`繫結](../functions/let-bindings.md)
