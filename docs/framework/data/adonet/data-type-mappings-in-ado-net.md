---
title: "ADO.NET でのデータ型のマッピング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a75914e032adf5b160724e17966b683a119b69a7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET でのデータ型のマッピング
.NET Framework は共通型システムを基にしています。このシステムは実行時の型の宣言、使用、および管理方法を定義するものです。 値型と参照型の両方から構成されており、これらはすべて <xref:System.Object> 基本型から派生します。 データ ソースを操作するときは、データ型が明示的に指定されていない場合はデータ プロバイダーから推論されます。 たとえば、<xref:System.Data.DataSet> オブジェクトは、特定のデータ ソースには依存しません。 `DataSet` 内のデータはデータ ソースから取得され、変更は `DataAdapter` によってデータ ソースに反映されます。 つまり、`DataAdapter` が <xref:System.Data.DataTable> 内の `DataSet` に、データ ソースからの値を格納すると、`DataTable` 内の列で結果として設定されるデータ型は、データ ソースへの接続を行う目的で使用した [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダー固有の型ではなく、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のデータ型になります。  
  
 同様に、`DataReader` がデータ ソースから値を返す場合、結果の値は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型のローカル変数に格納されます。 `Fill` の `DataAdapter` 操作と `Get` の `DataReader` メソッドのどちらの場合も、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の型は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーから返された値から推論されます。  
  
 返される値の型がわかっている場合は、推論されるデータ型を使用するのではなく、`DataReader` の型指定されたアクセサー メソッドを使用できます。 型指定されたアクセサー メソッドを使用して [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の特定の型として値を返すと、追加の型変換が不要になるため、パフォーマンスが向上します。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーのデータ型の null 値は、`DBNull.Value` で表現されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server データ型のマッピング](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.SqlClient> のデータ アクセサー メソッドを一覧で示します。  
  
 [OLE DB データ型のマッピング](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.OleDb> のデータ アクセサー メソッドを一覧で示します。  
  
 [ODBC データ型のマッピング](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.Odbc> のデータ アクセサー メソッドを一覧で示します。  
  
 [Oracle データ型のマッピング](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 推論されたデータ型マッピングおよび <xref:System.Data.OracleClient> のデータ アクセサー メソッドを一覧で示します。  
  
 [浮動小数点数](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 開発者が浮動小数点数を扱う際の発生頻度の高い問題について説明します。  
  
## <a name="see-also"></a>参照  
 [SQL Server データ型と ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [パラメーターおよびパラメーター データ型の構成](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [共通型システム](../../../../docs/standard/base-types/common-type-system.md)  
 [型の変換](http://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
