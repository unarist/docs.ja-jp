---
title: "XmlSchemaCollection スキーマのコンパイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# XmlSchemaCollection スキーマのコンパイル
**XmlSchemaCollection** は、XDR \(XML\-Data Reduced\) スキーマや XML スキーマ定義言語 \(XSD\) スキーマを格納および検証できるキャッシュ \(ライブラリ\) です。  **XmlSchemaCollection** は、ファイルや URL からスキーマにアクセスしなくて済むようにスキーマをメモリにキャッシュすることによって、パフォーマンスの向上を図ります。  
  
> [!NOTE]
>  **XmlSchemaCollection** クラスには XDR スキーマと XML スキーマの両方が格納されますが、**XmlSchema** オブジェクトを受け取ったり返したりするメソッドおよびプロパティは XML スキーマのみをサポートします。  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止されており、<xref:System.Xml.Schema.XmlSchemaSet> クラスに置き換えられています。  <xref:System.Xml.Schema.XmlSchemaSet> の詳細については、「[スキーマをコンパイルするための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)」を参照してください。  
  
## コレクションへのスキーマの追加  
 スキーマを **XmlSchemaCollection** に読み込むには、そのコレクションの **Add** メソッドを使用します。読み込み時に、スキーマは名前空間 URI に関連付けられます。  XML スキーマの場合、通常、この名前空間 URI がスキーマのターゲット名前空間になります。  また、XDR スキーマの場合は、この名前空間 URI は、スキーマがコレクションに追加されたときに指定された名前空間です。  
  
## コレクション内のスキーマの確認  
 スキーマがコレクション内にあるかどうかを確認するには、**Contains** メソッドを使用します。  **Contains** メソッドは、**XmlSchema** オブジェクト \(XML スキーマ専用\) またはスキーマに関連付けられた名前空間 URI を表す文字列 \(XML スキーマと XDR スキーマ用\) のいずれかを受け取ります。  
  
## コレクションからのスキーマの取得  
 コレクションからスキーマを取得するには、**Item** プロパティを使用します。  **Item** プロパティは、スキーマに関連付けられた名前空間 URI \(通常は、そのスキーマのターゲット名前空間\) を表す文字列を受け取り、**XmlSchema** オブジェクトを返します。  **Item** プロパティは、XML スキーマにだけ適用されます。  XDR スキーマの場合は、使用できるオブジェクト モデルがないため、戻り値は常に null 参照です。  
  
## XmlSchemaCollection を使用した XML ドキュメントの検証  
 **XmlSchemaCollection** を使用して XML インスタンス ドキュメントを検証するには、**XmlSchemaCollection** オブジェクトを作成し、開発者が作成したスキーマをそのコレクションに追加し、**XmlValidatingReader** の **Schemas** プロパティを設定して、作成した **XmlSchemaCollection** をその **XmlValidatingReader** に割り当てます。  
  
### パフォーマンスの向上  
 同じスキーマを基準として複数のドキュメントを検証する場合は、**XmlSchemaCollection** を使用することをお勧めします。このコレクションを使用すると、そのスキーマをメモリ内にキャッシュしてパフォーマンスの向上を図ることができます。  
  
 **XmlSchemaCollection** オブジェクトを作成し、そのコレクションにスキーマを追加し、**Schemas** プロパティを設定するコード サンプルを次に示します。  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## 参照  
 [XmlSchemaCollection を使用した XDR 検証](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)   
 [XmlSchemaCollection を使用した XML スキーマ \(XSD\) 検証](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)