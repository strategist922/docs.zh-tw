---
title: "程式碼引號 (F#)"
description: "了解 F # 程式碼引號，可讓您產生並以程式設計方式使用 F # 程式碼運算式的語言功能。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4559e659-2b04-48bd-8a0b-8527920eec95
ms.openlocfilehash: f7a08013bc6487b570a62576bb01ca2dd65ce8b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="code-quotations"></a>程式碼引號

> [!NOTE]
API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

本主題描述*程式碼引號*，可讓您產生並以程式設計方式使用 F # 程式碼運算式的語言功能。 這項功能可讓您產生抽象語法樹狀結構，表示 F # 程式碼。 可以周遊的抽象語法樹狀目錄，然後根據您的應用程式的需求來處理。 例如，您可以使用樹狀目錄中產生 F # 程式碼，或某些其他語言產生程式碼。


## <a name="quoted-expressions"></a>加上引號的運算式
A*加上引號運算式*是分隔的方式不會編譯為程式的一部分，但到 F # 運算式所表示的物件而是會編譯程式碼中的 F # 運算式。 您可以將標記的引號括住的運算式中有兩種： 使用型別資訊，或是不含類型資訊。 如果您想要包含的型別資訊，您會使用符號`<@`和`@>`來分隔引號括住的運算式。 如果您不需要型別資訊，您會使用符號`<@@`和`@@>`。 下列程式碼顯示具型別和不具類型的引號內。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet501.fs)]

周遊大型的運算式樹狀結構的速度如果您未包含型別資訊。 以具類型的符號括住的運算式的結果類型是`Expr<'T>`，而且型別參數都有 F # 編譯器的型別推斷演算法決定運算式的類型。 當您使用不含類型資訊的程式碼引號時，加上引號運算式的類型為非泛型型別[Expr](https://msdn.microsoft.com/library/ed6a2caf-69d4-45c2-ab97-e9b3be9bce65)。 您可以呼叫[Raw](https://msdn.microsoft.com/library/47fb94f1-e77f-4c68-aabc-2b0ba40d59c2)屬性的型別`Expr`類別來取得不具型別的`Expr`物件。

有各種不同的靜態方法，可讓您產生 F # 運算式物件以程式設計方式在`Expr`類別而不需要使用加上引號的運算式。

請注意，程式碼引號必須包含完整的運算式。 如`let`繫結，例如，您必須定義繫結的名稱和其他運算式使用之繫結。 詳細語法，在中，這是運算式所示`in`關鍵字。 在最上層模組中，這是只在模組中下, 一個運算式，但括在引號中，會明確所需。

因此，下列運算式不是有效的。

```fsharp
// Not valid:
// <@ let f x = x + 1 @>
```

但是，下列運算式會有效。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet502.fs)]

若要使用的程式碼引號，您必須加入匯入宣告 (使用`open`關鍵字)，就會開啟[Microsoft.FSharp.Quotations](https://msdn.microsoft.com/library/e9ce8a3a-e00c-4190-bad5-cce52ee089b2)命名空間。

F # PowerPack 評估與執行 F # 運算式物件，提供支援。


## <a name="expr-type"></a>Expr 的類型
執行個體`Expr`類型表示的 F # 運算式。 泛型和非泛型`Expr`類型都記錄於 F # 程式庫文件。 如需詳細資訊，請參閱[Microsoft.FSharp.Quotations 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.quotations-namespace-%5bfsharp%5d)和[Quotations.Expr 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/quotations.expr-class-%5bfsharp%5d)。


## <a name="splicing-operators"></a>接合運算子
接合，可讓您結合使用您建立以程式設計方式或從另一個程式碼引號運算式的常值的程式碼引號。 `%`和`%%`運算子可讓您將 F # 運算式物件新增到程式碼引號。 您使用`%`具類型的運算式物件插入具類型的引號的運算子; 您可以使用`%%`運算子來插入不具類型的引號不具類型的運算式物件。 這兩個運算子是一元前置運算子。 因此如果`expr`是不具類型的型別運算式`Expr`，下列程式碼就有效。

```fsharp
<@@ 1 + %%expr @@>
```

如果`expr`是具類型的型別引號`Expr<int>`，下列程式碼就有效。

```fsharp
<@ 1 + %expr @>
```

## <a name="example"></a>範例

### <a name="description"></a>描述
下列範例說明如何使用以 F # 程式碼置於運算式物件，並列印代表運算式的 F # 程式碼的程式碼引號。 函式`println`定義，其中包含遞迴函式`print`顯示 F # 運算式物件 (型別`Expr`) 的好記的格式。 有數個使用中的模式[Microsoft.FSharp.Quotations.Patterns](https://msdn.microsoft.com/library/093944a9-c752-403a-8983-5fcd5dbf92a4)和[Microsoft.FSharp.Quotations.DerivedPatterns](https://msdn.microsoft.com/library/d2434a6e-ae7b-4f3d-b567-c162938bc9cd)模組，可用於分析運算式物件。 此範例不包含所有可能模式可能會出現在 F # 運算式中。 任何無法辨識的觸發程序的萬用字元模式比對模式 (`_`) 和使用的呈現`ToString`方法，它會在`Expr`類型，可讓您知道要加入比對運算式的使用中模式。


### <a name="code"></a>程式碼
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet601.fs)]
    
### <a name="output"></a>輸出

```fsharp
fun (x:System.Int32) -> x + 1
a + 1
let f = fun (x:System.Int32) -> x + 10 in f 10
```

## <a name="example"></a>範例

### <a name="description"></a>說明
您也可以使用中的三個使用中模式[ExprShape 模組](https://msdn.microsoft.com/library/7685150e-2432-4d39-9338-57292eff18de)周遊使用較少的使用中模式的運算式樹狀架構。 當您想要周遊樹狀結構，但您不需要在大多數的節點中的所有資訊時，這些現用模式可能很有用。 當您使用這些模式時，任何 F # 運算式會比對下列三種模式的其中一個：`ShapeVar`如果運算式是一個變數，`ShapeLambda`如果運算式是 lambda 運算式或`ShapeCombination`如果運算式可以是任何其他項目。 如果您使用作用中的模式，如同先前的程式碼範例會周遊運算式樹狀架構，您必須使用許多的多個模式處理所有可能 F # 運算式型別，與您的程式碼將會更複雜。 如需詳細資訊，請參閱[ExprShape.ShapeVar &#124;ShapeLambda &#124;ShapeCombination 現用模式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/exprshape.shapevarhshapelambdahshapecombination-active-pattern-%5bfsharp%5d)。

下列程式碼範例可以用於做為基礎更複雜的周遊。 在這段程式碼，為包含函式呼叫的運算式建立運算式樹狀架構`add`。 [SpecificCall](https://msdn.microsoft.com/library/05a77b21-20fe-4b9a-8e07-aa999538198d)現用模式用於偵測的任何呼叫`add`運算式樹狀結構中。 此現用模式會指派至呼叫的引數`exprList`值。 在此情況下，有一些只有兩個，因此這些提取，且此函式就會遞迴呼叫的引數。 結果會插入到代表呼叫的程式碼引號`mul`使用接合運算子 (`%%`)。 `println`函式，從上一個範例用來顯示結果。

現用模式的其他分支中的程式碼只會重新產生相同的運算式樹狀架構，讓所產生的運算式中的唯一變更是從變更`add`至`mul`。


### <a name="code"></a>程式碼
[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet701.fs)]
    
### <a name="output"></a>輸出

```fsharp
1 + Module1.add(2,Module1.add(3,4))
1 + Module1.mul(2,Module1.mul(3,4))
```

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

