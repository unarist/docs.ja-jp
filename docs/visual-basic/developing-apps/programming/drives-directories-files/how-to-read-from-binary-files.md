---
title: "方法: Visual Basic でバイナリ ファイルを読み取る"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6056f7d33b1137abb19b24246ce6874ff4d008
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>方法: Visual Basic でバイナリ ファイルを読み取る
`My.Computer.FileSystem` オブジェクトには、バイナリ ファイルを読み取るための `ReadAllBytes` メソッドが用意されています。  
  
### <a name="to-read-from-a-binary-file"></a>バイナリ ファイルを読み取るには  
  
-   `ReadAllBytes` メソッドを使用します。このメソッドは、ファイルの内容をバイト配列として返します。 次のコードは、`C:/Documents and Settings/selfportrait.jpg` ファイルから読み取りを行う例です。  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   大きいバイナリ ファイルの場合は、<xref:System.IO.FileStream> オブジェクトの <xref:System.IO.FileStream.Read%2A> メソッドを使用して、一度に指定した量だけファイルから読み取ることができます。 その後、各読み取り操作でファイルからメモリに読み込まれる量を制限することができます。 次のコード例では、ファイルをコピーし、各読み取り操作でファイルからメモリに読み込まれる量を呼び出し元が指定できるようにします。  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   パスが無効である場合。1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
-   ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)  
  
-   文字列をバッファーに書き込むための十分なメモリがない (<xref:System.OutOfMemoryException>)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
 ファイル名からファイルの内容を判断しないでください。 たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。  
  
 アプリケーションでデータを使用する前に、入力をすべて検証してください。 ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [ファイルの読み取り](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [方法: 複数の書式を持つテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [クリップボードのデータの格納と読み取り](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
