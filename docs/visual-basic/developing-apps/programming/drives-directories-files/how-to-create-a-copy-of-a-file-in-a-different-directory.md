---
title: "方法 : Visual Basic でファイルのコピーを別のディレクトリに作成する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fe37ba940172e83574505d4c82e196f60dfc1eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>方法 : Visual Basic でファイルのコピーを別のディレクトリに作成する
`My.Computer.FileSystem.CopyFile` メソッドでは、ファイルをコピーできます。 このパラメーターでは、既存のファイルの上書き、ファイルの名前変更、操作の進行状況の表示、ユーザーによる操作のキャンセルが可能になります。  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>テキスト ファイルを別のフォルダーにコピーするには  
  
-   `CopyFile` メソッドを使用し、ソース ファイルとターゲット ディレクトリを指定してファイルをコピーします。 `overwrite` パラメーターでは、既存のファイルを上書きするかどうかを指定できます。 次のコード例では、`CopyFile` の使用方法を示します。  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   システムが絶対パスを取得できなかった (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
-   ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   結合したパスが、既存のディレクトリを指している (<xref:System.IO.IOException>)。  
  
-   リンク先ファイルが存在し、`overwrite` が `False` に設定されている (<xref:System.IO.IOException>)。  
  
-   ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.IO.IOException>)。  
  
-   同じ名前がターゲット フォルダー内のファイルで使用されている (<xref:System.IO.IOException>)。  
  
-   パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   `ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException`に設定され、ユーザーが操作をキャンセルしている (<xref:System.OperationCanceledException>)。  
  
-   `ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException` に設定され、未指定の I/O エラーが発生する (<xref:System.OperationCanceledException>)。  
  
-   パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [方法: 特定のパターンを持つファイルをディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [方法: ファイルのコピーを同じディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [方法: ディレクトリを別のディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [方法: ファイルの名前を変更する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
