---
title: ".NET Core で Microsoft XML Serializer Generator を使用する"
description: "Microsoft XML Serializer Generator の概要。"
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="bbf63-103">.NET Core で Microsoft XML Serializer Generator を使用する</span><span class="sxs-lookup"><span data-stu-id="bbf63-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="bbf63-104">このチュートリアルでは、C# .NET Core アプリケーションで Microsoft XML Serializer Generator を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="bbf63-105">このチュートリアルを通して、以下のことを学びます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="bbf63-106">.NET Core アプリの作成方法</span><span class="sxs-lookup"><span data-stu-id="bbf63-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="bbf63-107">Microsoft.XmlSerializer.Generator パッケージへの参照を追加する方法</span><span class="sxs-lookup"><span data-stu-id="bbf63-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="bbf63-108">MyApp.csproj を編集して依存関係を追加する方法</span><span class="sxs-lookup"><span data-stu-id="bbf63-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="bbf63-109">クラスと XmlSerializer を追加する方法</span><span class="sxs-lookup"><span data-stu-id="bbf63-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="bbf63-110">アプリケーションをビルドして実行する方法</span><span class="sxs-lookup"><span data-stu-id="bbf63-110">How to build and run the application</span></span> 

<span data-ttu-id="bbf63-111">.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard プロジェクト用の同等のものです。</span><span class="sxs-lookup"><span data-stu-id="bbf63-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="bbf63-112">アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bbf63-113">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="bbf63-113">Prerequisites</span></span>

<span data-ttu-id="bbf63-114">このチュートリアルを完了するには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="bbf63-114">To complete this tutorial:</span></span>

* <span data-ttu-id="bbf63-115">[.NET Core SDK 2.1.3 以降](https://www.microsoft.com/net/download) をインストールします</span><span class="sxs-lookup"><span data-stu-id="bbf63-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="bbf63-116">コード エディターをまだインストールしていなければ、お気に入りのエディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="bbf63-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="bbf63-117">コード エディターをインストールする必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="bbf63-117">Need to install a code editor?</span></span> <span data-ttu-id="bbf63-118">[Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) をお試しください。</span><span class="sxs-lookup"><span data-stu-id="bbf63-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="bbf63-119">.NET Core コンソール アプリケーションで Microsoft XML Serializer Generator を使用する</span><span class="sxs-lookup"><span data-stu-id="bbf63-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="bbf63-120">次の手順では、.NET Core コンソール アプリケーションで XML Serializer Generator を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="bbf63-121">.NET Core コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="bbf63-121">Create a .NET Core console application</span></span>

<span data-ttu-id="bbf63-122">コマンド プロンプトを開き、*MyApp* というフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="bbf63-123">作成したフォルダーに移動し、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="bbf63-124">MyApp プロジェクトで Microsoft.XmlSerializer.Generator パッケージへの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="bbf63-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="bbf63-125">[`dotnet add package`](../tools//dotnet-add-package.md) コマンドを使用して、プロジェクトで参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="bbf63-126">型:</span><span class="sxs-lookup"><span data-stu-id="bbf63-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="bbf63-127">パッケージを追加した後に MyApp.csproj の変更を確認する</span><span class="sxs-lookup"><span data-stu-id="bbf63-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="bbf63-128">コード エディターを開き、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="bbf63-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="bbf63-129">引き続き、アプリをビルドした *MyApp* ディレクトリから作業します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="bbf63-130">テキスト エディターで *MyApp.csproj* を開きます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="bbf63-131">[`dotnet add package`](../tools//dotnet-add-package.md) コマンドを実行すると、以下の行が *MyApp.csproj* プロジェクト ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="bbf63-132">.NET Core CLI Tool のサポートのために別の ItemGroup セクションを追加する</span><span class="sxs-lookup"><span data-stu-id="bbf63-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="bbf63-133">検査した `ItemGroup` セクションの後に以下の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="bbf63-134">アプリケーションにクラスを追加する</span><span class="sxs-lookup"><span data-stu-id="bbf63-134">Add a class in the application</span></span>

<span data-ttu-id="bbf63-135">テキスト エディターで *Program.cs* を開きます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="bbf63-136">*MyClass* というクラスを *Program.cs* に追加します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="bbf63-137">MyClass 用の `XmlSerializer` を作成する</span><span class="sxs-lookup"><span data-stu-id="bbf63-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="bbf63-138">*Main* 内に次の行を追加して MyClass 用の `XmlSerializer` を作成します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="bbf63-139">アプリケーションのビルドと実行</span><span class="sxs-lookup"><span data-stu-id="bbf63-139">Build and run the application</span></span>

<span data-ttu-id="bbf63-140">*MyApp* フォルダー内のままで、[`dotnet run`](../tools/dotnet-run.md) を介してアプリケーションを実行すると、事前生成されたシリアライザーが実行時に自動的に読み込まれ、使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="bbf63-141">コンソール ウィンドウに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="bbf63-142">[`dotnet run`](../tools/dotnet-run.md) は、[`dotnet build`](../tools/dotnet-build.md) を呼び出してビルド ターゲットがビルドされていることを確認した後、`dotnet <assembly.dll>` を呼び出してターゲット アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="bbf63-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbf63-143">このチュートリアルで紹介した、アプリケーションを実行するコマンドと手順は、開発時にのみ利用されます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="bbf63-144">アプリの展開に進むときは、.NET Core アプリの別の[展開方法](../deploying/index.md)や [`dotnet publish`](../tools/dotnet-publish.md) コマンドを利用した方が効果的な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bbf63-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="bbf63-145">すべて正常に終了すると、*MyApp.XmlSerializers.dll* というアセンブリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="bbf63-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="bbf63-146">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="bbf63-146">Congratulations!</span></span> <span data-ttu-id="bbf63-147">今回の成果:</span><span class="sxs-lookup"><span data-stu-id="bbf63-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="bbf63-148">.NET Core アプリを作成しました。</span><span class="sxs-lookup"><span data-stu-id="bbf63-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="bbf63-149">Microsoft.XmlSerializer.Generator パッケージへの参照を追加しました。</span><span class="sxs-lookup"><span data-stu-id="bbf63-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="bbf63-150">MyApp.csproj を編集して依存関係を追加しました。</span><span class="sxs-lookup"><span data-stu-id="bbf63-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="bbf63-151">クラスと XmlSerializer を追加しました。</span><span class="sxs-lookup"><span data-stu-id="bbf63-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="bbf63-152">アプリケーションをビルドして実行しました。</span><span class="sxs-lookup"><span data-stu-id="bbf63-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="bbf63-153">関連資料</span><span class="sxs-lookup"><span data-stu-id="bbf63-153">Related Resources</span></span>

* [<span data-ttu-id="bbf63-154">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="bbf63-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="bbf63-155">方法: XmlSerializer を使用してシリアル化する (C#)</span><span class="sxs-lookup"><span data-stu-id="bbf63-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [<span data-ttu-id="bbf63-156">方法: XmlSerializer を使用してシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbf63-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)