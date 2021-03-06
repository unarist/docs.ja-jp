---
title: "XML ツリー (LINQ to XML) の変更 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de66788186f3ffd09560d8eacdebbbaa5edf067c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a>XML ツリー (LINQ to XML) の変更 (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] は、XML ツリーのメモリ内ストアです。 ソースから XML ツリーを読み込んだり解析したりした後に、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用してツリーを直接変更することができます。その後、ツリーをシリアル化して、ファイルに保存したり、リモート サーバーに送信したりできます。  
  
 ツリーを直接変更する際には、<xref:System.Xml.Linq.XContainer.Add%2A> などの特定のメソッドを使用します。  
  
 ただし、これには別の方法もあります。それは、関数型構築を使用して、別の新しいツリーを生成する方法です。 XML ツリーに対する変更の種類やツリーのサイズによっては、この方法の方が堅牢で、開発も容易になります。 このセクションの最初のトピックでは、この 2 つの方法を比較します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[メモリ内の XML ツリーの変更と関数型構築 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|XML ツリーのメモリ内での変更と関数型構築とを比較します。|  
|[XML ツリー (Visual Basic) への要素、属性、およびノードの追加](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|XML ツリーへの要素、属性、またはノードの追加に関する情報について説明します。|  
|[XML ツリー内の要素、属性、およびノードの変更](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|既存の要素、属性、またはノードの変更に関する情報について説明します。|  
|[(Visual Basic) の XML ツリーから要素、属性、およびノードの削除](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|XML ツリーからの要素、属性、またはノードの削除に関する情報について説明します。|  
|[名前/値ペア (Visual Basic) を維持します。](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|アプリケーションの情報を名前/値のペアとして保持する方法について説明します。このような情報には、構成情報やグローバル設定があります。|  
|[方法: Namespace、全体 XML ツリーを変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|XML ツリーを名前空間の間で移動する方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [プログラミング ガイド (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
