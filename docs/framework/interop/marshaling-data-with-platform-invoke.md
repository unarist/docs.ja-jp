---
title: "プラットフォーム呼び出しによるデータのマーシャリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24ae6da0b32cf15ee9104bd10ba5fe6bb03a9763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-data-with-platform-invoke"></a>プラットフォーム呼び出しによるデータのマーシャリング
アンマネージ ライブラリからエクスポートされた関数を呼び出すには、.NET Framework アプリケーションで、マネージ コード内にアンマネージ関数を表す関数プロトタイプが必要です。 プラットフォーム呼び出しがデータを正しくマーシャリングできるようにするプロトタイプを作成するには、次のことを実行する必要があります。  
  
-   <xref:System.Runtime.InteropServices.DllImportAttribute> 属性をマネージ コード内の静的関数またはメソッドに適用します。  
  
-   アンマネージ データ型をマネージ データ型に置き換えます。  
  
 アンマネージ関数に付属のドキュメントを使用して、属性とその省略可能なフィールドを適用し、アンマネージ型をマネージ データ型に置き換えることによって、同等のマネージ プロトタイプを作成できます。 **DllImportAttribute** を適用する方法の詳細については、「[アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)」を参照してください。  
  
 このセクションでは、アンマネージ ライブラリによってエクスポートされた関数に引数を渡し、その関数からの戻り値を受け取るための、マネージ関数のプロトタイプを作成する方法を示すサンプルを示します。 サンプルではまた、いつ <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性と <xref:System.Runtime.InteropServices.Marshal> クラスを使用して明示的にデータをマーシャリングするかをも示しています。  
  
## <a name="platform-invoke-data-types"></a>プラットフォーム呼び出しのデータ型  
 次の表は、Win32 API (Wtypes.h にリストされている) と C スタイルの関数で使用されるデータ型を一覧で示しています。 多くのアンマネージ ライブラリには、これらのデータ型をパラメーターや戻り値として渡す関数が含まれています。 3 番目の列には、マネージ コードで使用する、対応する .NET Framework の組み込みの値型またはクラスを一覧で示します。 場合によっては、表にリストされた型を、同じサイズの型に置き換えることができます。  
  
|Wtypes.h でのアンマネージ型|アンマネージ C 言語型|マネージ クラス名|説明|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**HANDLE**|**void\***|<xref:System.IntPtr?displayProperty=nameWithType>|32 ビット Windows オペレーティング システム、64 ビット Windows オペレーティング システムで 64 ビットに 32 ビットです。|  
|**BYTE**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 ビット|  
|**SHORT**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 ビット|  
|**WORD**|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|16 ビット|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32 ビット|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32 ビット|  
|**LONG**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32 ビット|  
|**BOOL**|**long**|<xref:System.Byte>|32 ビット|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 ビット|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32 ビット|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|ANSI で装飾します。|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Unicode で装飾します。|  
|**LPSTR**|**char\***|<xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI で装飾します。|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType>|ANSI で装飾します。|  
|**LPWSTR**|**wchar_t\***|<xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode で装飾します。|  
|**LPCWSTR**|**Const wchar_t\***|<xref:System.String?displayProperty=nameWithType> または <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Unicode で装飾します。|  
|**FLOAT**|**Float**|<xref:System.Single?displayProperty=nameWithType>|32 ビット|  
|**DOUBLE**|**Double**|<xref:System.Double?displayProperty=nameWithType>|64 ビット|  
  
 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C#、および C++ での対応する型については、「[.NET Framework クラス ライブラリの概要](../../../docs/standard/class-library-overview.md)」を参照してください。  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 次のコードでは、Pinvoke.dll によって提供されるライブラリ関数を定義します。 このセクションで説明される多くのサンプルでは、このライブラリを呼び出します。  
  
### <a name="example"></a>例  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
