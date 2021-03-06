---
title: "文字データ型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1066444ba3a98f26fc2a35135a50b2954c6b992
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="character-data-types-visual-basic"></a>文字データ型 (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供*文字データ型*文字や表示可能な文字を処理します。 Unicode 文字を扱う両者間`Char`一方、1 つの文字を保持している`String`不特定数文字にはが含まれています。  
  
 サイド バイ サイドの比較を表示するテーブルの[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)です。  
  
## <a name="char-type"></a>Char 型  
 `Char`データ型は単一 2 バイト (16 ビット) の Unicode 文字。 変数は、常に正確に 1 つの文字を保存する場合として宣言`Char`です。 例:  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 使用可能な各値、`Char`または`String`変数は、*コード ポイントが*、または Unicode 文字セット内の文字コード。 Unicode 文字には、基本的な ASCII 文字セット、さまざまな他のアルファベット文字、アクセント記号、通貨記号、分数、分音文字、および数学と技術的な記号が含まれます。  
  
> [!NOTE]
>  Unicode 文字セットは、コード ポイント D800 ~ DFFF (55551 を通じて 55296) の*サロゲート ペア*、1 つのコード ポイントを表す 2 つの 16 ビット値を必要とします。 A`Char`変数は、サロゲート ペアを保持できないと`String`2 つの位置を使用してこのようなペアを保持します。  
  
 詳細については、次を参照してください。 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)です。  
  
## <a name="string-type"></a>文字列型  
 `String`データ型は、0 個以上 2 バイト (16 ビット) の Unicode 文字のシーケンス。 場合は、変数は、不特定数の文字を含めることができます、宣言として`String`です。 例:  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 詳細については、次を参照してください。[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)です。  
  
## <a name="see-also"></a>関連項目  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
