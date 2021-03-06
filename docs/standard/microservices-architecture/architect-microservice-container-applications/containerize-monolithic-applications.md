---
title: "Containerizing モノリシック アプリケーション"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Containerizing モノリシック アプリケーション"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 11e2c24403b9b61584e424696c844e00e5d34b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="containerizing-monolithic-applications"></a>Containerizing モノリシック アプリケーション

Monolithically 展開された、1 つの web アプリケーションまたはサービスをビルドし、コンテナーとして展開する場合があります。 アプリケーション自体は内部的にモノリシックできない可能性がありますが、いくつかのライブラリ、コンポーネント、または (アプリケーション レイヤーでドメイン層、データ アクセス層など) でもレイヤーを構造化します。 外部で、ただし、これは 1 つのコンテナー-1 つのプロセス、1 つの web アプリケーション、または 1 つのサービスです。

このモデルを管理するには、アプリケーションを表すための 1 つのコンテナーを展開します。 スケール アップ、だけをロード バランサーを前面にでより多くのコピーを追加します。 簡単な 1 つのコンテナーまたは VM で単一の展開の管理に由来します。

![](./media/image1.png)

**図 4-1**です。 モノリシック コンテナー化アプリケーションのアーキテクチャの例

図 4-1 に示すように各コンテナーに複数のコンポーネント、ライブラリ、または内部のレイヤーを含めることができます。 ただし、このモノリシックなパターンがあります競合「コンテナーは、1 つし、1 つのプロセスでは、」可能性があるコンテナーの原則を使用する一部のケース [ok] です。

このアプローチの欠点は、拡張を必要とするアプリケーションが増加する場合に顕著になります。 アプリケーション全体が拡張可能である場合は本当に問題 ただし、ほとんどの場合、アプリケーションのいくつかの部分はスケーリングを必要とする他のコンポーネントがときに使用される小さいチョーク ポイント。

たとえば、一般的な e コマース アプリケーションで可能性がありますのでが必要、製品情報サブシステムを拡張する購入するよりも多くのユーザーが製品を参照します。 支払パイプラインを使用するより多くの顧客は、バスケットを使用します。 少ない顧客は、コメントを追加または、購入履歴を表示します。 コンテンツやマーケティング キャンペーンを管理する必要がある従業員のほんの一部のみがある可能性があります。 モノリシックな設計を拡張する場合、これらのさまざまなタスクのすべてのコードが複数回の展開され、同じグレードに拡大/縮小します。

アプリケーションの拡張をいくつかの方法: 水平方向の重複、アプリケーション、およびパーティション分割のようなビジネスの概念やデータのさまざまな領域を分割します。 ただし、すべてのコンポーネントのスケーリングの問題、に加えて 1 つのコンポーネントへの変更を必要と、アプリケーション全体とすべてのインスタンスの再配置の完了の完全な再テストします。

ただし、モノリシックなアプローチが一般的では、アプリケーションの開発は microservices アプローチを最初により簡単です。 したがって、多くの組織は、このアーキテクチャのアプローチを使用して開発します。 一部の組織は、十分な結果良いいたが、間に制限他ヒットします。 多くの組織には、ツールとインフラストラクチャ困難になることもサービスを構築する指向アーキテクチャ (SOA) 年前に、および成功必要性が確認できなかったために、このモデルを使用して、アプリケーションが設計されています: アプリケーションが拡張されるまでです。

インフラストラクチャの観点からは、各サーバーは、同じホスト内で多くのアプリケーションを実行し、図 4-2 に示すように、リソース使用量の効率性の許容の比率があります。

![](./media/image2.png)

**図 4-2**です。 モノリシックなアプローチ各アプリのコンテナーとして実行されているホストの複数のアプリを実行している。

Microsoft Azure での単一のアプリケーションは、インスタンスごとに専用の仮想マシンを使用して展開できます。 さらを使用して[Azure VM スケール セット](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)Vm を簡単に拡張することができます。 [Azure App Service](https://azure.microsoft.com/services/app-service/)もモノリシックなアプリケーションを実行し、Vm を管理することがなく、インスタンスを簡単にスケールできます。 2016 年以降、Azure アプリ サービスは、特定の展開を簡略化することも、Docker のコンテナーの単一のインスタンスを実行できます。

QA 環境または限定された運用環境では、複数の Docker ホストの Vm を展開し、図 4-3 に示すように、Azure の負荷分散装置を使用してそれらのバランスをとることがことができます。 これにより、粒度が粗いアプローチを使用したスケールを管理するため、アプリケーション全体が 1 つのコンテナー内に存在できます。

![](./media/image3.png)

**図 4-3**です。 複数のホストを 1 つのコンテナー アプリケーションのスケール アップの例

さまざまなホストへの展開は、従来の展開方法で管理できます。 などのコマンドで docker ホストを管理できる`docker run`または`docker-compose`手動、または継続的な配信 (CD) パイプラインなどのオートメーションによってを実行します。

## <a name="deploying-a-monolithic-application-as-a-container"></a>コンテナーとしてモノリシックなアプリケーションを配置します。

モノリシックなアプリケーション展開を管理するコンテナーを使用する利点があります。 コンテナーのインスタンスをスケール、はるかに高速化およびその他の Vm をデプロイするよりも簡単です。 VM スケール セットを使用する場合でも、起動に時間がかかり Vm です。 コンテナーではなく、従来のアプリケーション インスタンスとして展開されると、アプリケーションの構成は、VM の一部として管理はこれは理想的ではありません。

Docker images がはるかに高速更新の展開とネットワーク効率的です。 Docker イメージ通常起動 (秒単位) の展開の速度が向上します。 発行元と同じくらい簡単設定解除を行う Docker イメージのインスタンスは、`docker stop`コマンドを使用し、通常、1 秒未満で完了します。

コンテナーがデザインが変更可能なことはありません、破損している Vm について心配する必要があります。 これに対し、VM の更新スクリプトは、いくつかの特定の構成またはファイルがディスク上の残りのアカウントを忘れた可能性があります。

モノリシック アプリケーションにとって有益な Docker、メリットにのみお接触します。 他のコンテナーを管理する利点は、コンテナー orchestrators は、さまざまなインスタンスと各コンテナー インスタンスのライフ サイクル管理と展開から取得されます。 Microservices の領域へのエントリ ポイントは、スケール、開発、および個別に展開できるサブシステムにモノリシックなアプリケーションを分割します。

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Azure App Service に単一のコンテナーをベースのアプリケーションの発行

Azure にデプロイされたコンテナーの検証を取得するかどうか、またはアプリケーションが単一コンテナー アプリケーションだけである場合は、Azure App Service は、単一コンテナー ベースでのスケーラブルなサービスを提供する優れた方法を提供します。 Azure App Service を使用することは簡単です。 コードを取得し、Visual Studio でビルドし、Azure に直接展開が簡単に Git を使用した優れた統合を提供します。

![](./media/image4.png)

**図 4-4**です。 Visual Studio から Azure App Service に単一コンテナー アプリケーションの発行

Docker, せず他の機能、フレームワーク、または Azure App Service でサポートされていない依存関係が必要な場合必要がありました Azure チームは、App Service でそれらの依存関係を更新するまで待機します。 または、他のサービスを Azure Service Fabric、Azure クラウド サービス、またはであっても、その Vm をさらに制御があり、アプリケーションの必要なコンポーネントまたはフレームワークをインストールする可能性がありますに切り替える必要がありました。

Visual Studio 2017 でコンテナー サポートでは、図 4-4 に示すように、アプリケーション環境に自由に含める機能を提供します。 設定されているために、コンテナーで、アプリケーションに依存関係を追加する場合、Dockerfile または Docker イメージの依存関係を含めることができます。

表示されている図 4-4、としては、発行フローは、コンテナー レジストリを使用してイメージをプッシュします。 これは、Azure コンテナー レジストリ (レジストリは、Azure でデプロイを閉じるし、Azure Active Directory グループとアカウントによって保護された) または Docker Hub または内部設置型レジストリなどの他の Docker レジストリに指定できます。


>[!div class="step-by-step"]
[前](index.md) [次へ] (docker-アプリケーションの状態-data.md)
