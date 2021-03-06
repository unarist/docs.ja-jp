---
title: "クレームとトークン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2e571e8526581269cedb65b83c9ea0d8a81e280
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-tokens"></a>クレームとトークン
ここでは、サポートされている既定のトークンから [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] によって作成されるさまざまなクレームの種類について説明します。  
  
 クライアント資格情報のクレームは、<xref:System.IdentityModel.Claims.ClaimSet> クラスと <xref:System.IdentityModel.Claims.Claim> クラスを使用して確認できます。 `ClaimSet` には、`Claim` オブジェクトのコレクションが格納されます。 各 `Claim` には、次の重要なメンバーがあります。  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> プロパティは、作成されるクレームの種類を指定する URI (Uniform Resource Identifier) を返します。 たとえば、クレームの種類が証明書の拇印の場合、その URI は http:schemas.microsoft.com/ws/20005/05/identity/claims/thumprint です。  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティは、クレームの権限を指定する URI を返します。 定義済みの権限は、<xref:System.IdentityModel.Claims.Rights> クラスにあります (<xref:System.IdentityModel.Claims.Rights.Identity%2A>、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>)。  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> プロパティは、クレームに関連付けられているリソースを返します。  
  
 各 <xref:System.IdentityModel.Claims.ClaimSet> には、<xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> プロパティがあり、それぞれ <xref:System.IdentityModel.Claims.ClaimSet> の `Issuer` を表します。  
  
## <a name="windows-accounts"></a>Windows アカウント  
 クライアント資格情報が Windows ユーザー アカウントにマップされる場合、<xref:System.IdentityModel.Claims.ClaimSet> は次の値を格納します。  
  
-   `Issuer` は、<xref:System.IdentityModel.Claims.ClaimSet> クラスの静的 Windows プロパティによって返される値です。  
  
-   コレクションには次のクレームがあります。  
  
    -   <xref:System.IdentityModel.Claims.Claim> 値がセキュリティ識別子 (SID)、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> プロパティ値が <xref:System.IdentityModel.Claims.Claim.Right%2A> で、`Identity` が実際の SID 値を返す <xref:System.IdentityModel.Claims.Claim.Resource%2A>。 SID は、ドメイン コントローラーによって各ユーザーに発行される一意の値です。 SID は、Windows セキュリティとの対話でユーザーを識別するために使用されます。  
  
    -   <xref:System.IdentityModel.Claims.Claim> 値 が SID、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> が <xref:System.IdentityModel.Claims.Claim.Right%2A> で、`PossessProperty` が SID 値の <xref:System.IdentityModel.Claims.Claim.Resource%2A>。  
  
    -   <xref:System.IdentityModel.Claims.Claim> が <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>、<xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> が <xref:System.IdentityModel.Claims.Claim.Right%2A> で、`PossessProperty` がユーザー名 (たとえば、"MYMACHINE\Bob") を含んだ文字列である <xref:System.IdentityModel.Claims.Claim.Resource%2A>。  
  
    -   ユーザーが属するさまざまなグループの <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> が指定された追加の SID クレーム。  
  
## <a name="certificates"></a>証明書  
 クライアント資格情報が証明書の場合、<xref:System.IdentityModel.Claims.ClaimSet> は次の値を格納します。  
  
-   自己発行証明書の場合、`Issuer` は <xref:System.IdentityModel.Claims.ClaimSet> です。 <xref:System.IdentityModel.Claims.ClaimSet> は、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> に設定された <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> に設定された `Identity`、および証明書の拇印を含んだ <xref:System.IdentityModel.Claims.Claim.Resource%2A> 配列である <xref:System.Byte> 値を返します。  
  
-   証明機関によって発行された証明書の場合、発行者は、証明機関の証明書を表す `ClaimSet` です。  
  
-   コレクションの `Claims` には次のものが含まれます。  
  
    -   `Claim` が Thumbprint、`ClaimType` が PossessProperty で、`Right` が証明書の拇印を含んだバイト配列である `Resource`。  
  
    -   証明書のさまざまなプロパティを表す X500DistinguishedName、Dns、Name、Upn、Rsa などの複数の種類の追加の PossessProperty クレーム。 Rsa クレームのリソースは、証明書に関連付けられている公開キーです。**注**クライアント資格情報の種類が Windows をサービスにマップする証明書をアカウント、2 つ`ClaimSet`オブジェクトが生成されます。 最初のオブジェクトには、Windows アカウントに関するすべてのクレームが入り、2 番目のオブジェクトには、証明書に関するすべてのクレームが入ります。  
  
## <a name="user-namepassword"></a>ユーザー名/パスワード  
 クライアント資格情報が、Windows アカウントにマップされないユーザー名とパスワード (または同等のもの) の場合、`ClaimSet` は、<xref:System.IdentityModel.Claims.ClaimSet.System%2A> クラスの静的 `ClaimSet` プロパティによって発行されます。 `ClaimSet`が含まれています、`Identity`要求の種類の<xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>リソースがクライアントのユーザー名を提供します。 対応するクレームには、`Right` の`PossessProperty` があります。  
  
## <a name="rsa-keys"></a>RSA キー  
 証明書に関連付けられていない RSA キーを使用すると、場所、結果として得られる`ClaimSet`は、自己発行し、が含まれています、`Identity`要求の種類の<xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>リソースが RSA キーです。 対応するクレームには、`Right` の`PossessProperty` があります。  
  
## <a name="saml"></a>SAML  
 クライアントが SAML (Security Assertions Markup Language) トークンを使用して認証する場合、`ClaimSet` は、SAML トークンを署名したエンティティ (通常は、SAML トークンを発行したセキュリティ トークン サービス (STS) の証明書) によって発行されます。 `ClaimSet` は、SAML トークンに含まれているとおりのさまざまなクレームを格納します。 SAML トークンが、名前が `SamlSubject` 以外の `null` を含んでいる場合、型が `Identity` で、リソース型が <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> の <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> クレームが作成されます。  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Identity クレームと ServiceSecurityContext.IsAnonymous  
 None の場合、`ClaimSet`クライアントの資格情報の結果オブジェクトはクレームを格納、`Right`の`Identity,`、<xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>プロパティから返される`true`です。 このようなクレームが 1 つ以上ある場合、`IsAnonymous` プロパティは `false` を返します。  
  
## <a name="see-also"></a>参照  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
