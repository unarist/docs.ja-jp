---
title: "セキュリティ例外"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 431226f8ce56300f83df64a713b477f0065e2f56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-exceptions"></a>セキュリティ例外
ここでは、すべてのセキュリティ例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|このサービスでは匿名ログオンは許可されていません。|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|要求メッセージは保護される必要があります。 これは指定されたコントラクトの操作で必要です。 指定されたバインディングで保護される必要があります。|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|応答メッセージは保護される必要があります。 これは指定されたコントラクトの操作で必要です。 指定されたバインディングで保護される必要があります。|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|セキュリティ ヘッダーに指定できるプライマリ署名は 1 つだけです。|  
|BadContextTokenFaultReason|セキュリティ コンテキスト トークンが期限切れであるか無効です。 メッセージは処理されませんでした。|  
|BadEncryptionState|EncryptedData または EncryptedKey は、この操作に対して無効な状態です。|  
|BasicHttpMessageSecurityRequiresCertificate|BasicHttp のバインディングでは、メッセージをセキュリティで保護するために BasicHttpBinding.Security.Message.ClientCredentialType が BasicHttpMessageCredentialType.Certificate 資格情報型と等しいことが要求されています。 UserName 資格情報には、Transport または TransportWithMessageCredential セキュリティを選択してください。|  
|BasicTokenCannotBeWrittenWithoutEncryption|基本トークンを暗号化せずに書き込むことはできません。|  
|BindingDoesNotSupportProtectionForRst|指定されたコントラクトの指定されたバインディングには SecureConversation が構成されていますが、この認証モードでは、ネゴシエーションに必要な要求/応答ベースの整合性と機密性を実現できません。|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|自動的に偽装を行うには指定されたコントラクト操作に Windows ID が必要です。 呼び出し元を表す Windows ID が、指定されたコントラクトの指定されたバインディングによって提供されていません。|  
|CachedNegotiationStateQuotaReached|容量が指定された制限に達したため、サービスがネゴシエーションの状態をキャッシュできません。 要求を再試行してください。|  
|CacheQuotaReached|項目を追加できません。 キャッシュの最大サイズが指定されています。|  
|CannotDetermineSPNBasedOnAddress|クライアントは、SspiNegotiation/Kerberos に使用される指定された対象アドレスの ID から、サービス プリンシパル名を特定できません。 対象アドレス id は、UPN id である必要があります (acmedomain など\\\alice) または SPN id (ホスト/振り-)。|  
|CannotFindCert|StoreName、StoreLocation、FindType、FindValue という検索条件で検索しましたが、X.509 証明書が見つかりません。|  
|CannotFindCertForTarget|指定された対象の StoreName、StoreLocation、FindType、FindValue という、指定された検索条件で検索しましたが、X.509 証明書が見つかりません。|  
|CannotFindCorrelationStateForApplyingSecurity|応答側の応答にセキュリティを適用するために必要な相関状態が見つかりません。|  
|CannotFindNegotiationState|指定されたコンテキストのネゴシエーションの状態が見つかりません。|  
|CannotFindSecuritySession|指定された ID を持つセキュリティ セッションが見つかりません。|  
|CannotImportProtectionLevelForContract|プロセスをインポートするポリシーが指定されたコントラクトのバインディングをインポートできません。 このバインディングの保護要件は、このコントラクトについて既にインポートされたバインディングに適合していません。 このバインディングを構成し直す必要があります。|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|セキュリティ ポリシーのインポートに失敗しました。 このセキュリティ ポリシーには、操作範囲にサポート トークン要件が含まれています。 コントラクトの説明では、この操作に関連付けられている要求メッセージに対するアクションが指定されていません。|  
|CannotIssueRstTokenType|トークンまたは指定された型を発行できません。|  
|CannotObtainIssuedTokenKeySize|発行されたトークンのキー サイズを特定できません。|  
|CannotPerformImpersonationOnUsernameToken|クライアント トークンを使用した偽装はできません。 指定されたコントラクトの指定されたバインディングでは、登録済みのメンバーシップ プロバイダーによるクライアント認証にユーザー名セキュリティ トークンを使用します。 クライアント用に別の種類のセキュリティ トークンを使用してください。|  
|CannotPerformS4UImpersonationOnPlatform|指定されたコントラクトの指定されたバインディングは、[!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] 以降のバージョンの Windows でのみ偽装をサポートします。 SspiNegotiated 認証とキャンセルを有効にした SecureConversation を使用したバインディングを使用してください。|  
|CannotReadKeyIdentifier|指定された名前空間を持つ指定された要素から KeyIdentifier を読み取ることができません。|  
|CannotReadToken|指定された ValueType が設定された BinarySecretSecurityToken の、指定された名前空間を持つ指定された要素からトークンを読み取ることができません。 この要素が有効であることが要求される場合は、指定された名前、名前空間、および値の型のトークンを使用するようにセキュリティが構成されていることを確認してください。|  
|CertificateUnsupportedForHttpTransportCredentialOnly|証明書ベースのクライアント認証は TransportCredentialOnly セキュリティ モードではサポートされません。 Transport セキュリティ モードを選択してください。|  
|ClaimTypeCannotBeEmpty|claimType を空の文字列にすることはできません。|  
|ClientCertificateNotProvided|クライアントの証明書が提供されていません。 証明書は、ClientCredentials または ServiceCredentials で設定できます。|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType.None は、TransportWithMessageCredential セキュリティ モードでは無効です。 資格情報の種類を指定するか、別のセキュリティ モードを使用してください。|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|この構成スキーマは、次のセキュリティ バインド要素の非標準構成を記述するには不十分です:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|派生キーの指定された世代と長さに問題があるため、キー派生オフセットが許可されている最大オフセットを超えています。|  
|DnsIdentityCheckFailedForIncomingMessage|受信メッセージの ID 検査が失敗しました。 リモート エンドポイントの予測されたドメイン ネーム システム (DNS) ID は既に指定されています。 リモート エンドポイントから提供されたのは、指定されたドメイン ネーム システム (DNS) クレームでした。 これが適正なリモート エンドポイントである場合は、チャネルのプロキシを作成する際に、ドメイン ネーム システム ID を EndpointAddress の ID プロパティとして指定することで問題を修正できます。|  
|DnsIdentityCheckFailedForOutgoingMessage|送信メッセージの ID の確認に失敗しました。リモート エンドポイントには、指定されたドメイン ネーム システム ID が必要でした。 リモート エンドポイントから提供されたのは、ドメイン ネーム システム (DNS) クレームでした。 これが適正なリモート エンドポイントである場合は、チャネルのプロキシを作成する際に、DNS ID を EndpointAddress の ID プロパティとして明示的に指定することで問題を修正できます。|  
|DuplicateIdInMessageToBeVerified|検証対象のメッセージに、指定された ID が 2 つあります。|  
|EmptyBase64Attribute|必須の Base64 属性名と名前空間に対して空の値が見つかりました。|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|セキュリティ ポリシーをエクスポートできませんでした。 このバインディングには、AsymmetricSecurityBindingElement とセキュリティで保護されたトランスポート バインド要素の両方が指定されています。 このようなバインド用のポリシーのエクスポートはサポートされていません。|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|セキュリティ ポリシーをエクスポートできませんでした。 このバインディングには、SymmetricSecurityBindingElement とセキュリティで保護されたトランスポート バインド要素の両方が指定されています。 このようなバインド用のポリシーのエクスポートはサポートされていません。|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|セキュリティ ポリシーをエクスポートできませんでした。 このバインディングには、TransportSecurityBindingElement が指定されていますが、ITransportTokenAssertionProvider を実装するトランスポート バインド要素がありません。 このようなバインド用のポリシーのエクスポートはサポートされていません。 バインディングに ITransportTokenAssertionProvider インターフェイスを実装するトランスポート バインド要素を設定してください。|  
|FoundMultipleCerts|StoreName、StoreLocation、FindType、FindValue という検索条件で検索しましたが、複数の X.509 証明書が見つかりました。 より具体的な検索条件を指定してください。|  
|FoundMultipleCertsForTarget|指定された対象の StoreName、StoreLocation、FindType、FindValue という、指定された検索条件で検索したところ、複数の X.509 証明書が見つかりました。 より具体的な検索条件を指定してください。|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion.WSSecurityJan2004 は、ヘッダーの解読をサポートしていません。 SecurityVersion.WsSecurityXXX2005 以降を使用するか、トランスポート セキュリティを使用してメッセージ全体を暗号化してください。|  
|IdentityCheckFailedForIncomingMessage|受信メッセージの ID 検査が失敗しました。 予測される ID が対象エンドポイントに指定されています。|  
|IdentityCheckFailedForOutgoingMessage|送信メッセージの ID の確認が失敗しました。 予測される ID が対象エンドポイントに指定されています。|  
|IncorrectSpnOrUpnSpecified|SSPI (Security Support Provider Interface) 認証が失敗しました。 サーバーが、指定された ID を持つアカウントで実行されていない可能性があります。 サーバーがサービス アカウント (ネットワーク サービスなど) で実行されている場合は、そのアカウントの ServicePrincipalName をサーバーの EndpointAddress で ID として指定してください。 サーバーがユーザー アカウントで実行されている場合は、そのアカウントの UserPrincipalName をサーバーの EndpointAddress で ID として指定してください。|  
|InvalidAttributeInSignedHeader|指定された署名済みヘッダーには指定された属性が含まれています。 必要な属性が指定されています。|  
|InvalidCloseResponseAction|指定された無効なアクションによってセキュリティ セッションの終了応答を受信しました。|  
|InvalidQName|この QName は無効です。|  
|InvalidRenewResponseAction|指定された無効なアクションによってセキュリティ セッションの更新応答を受信しました。|  
|InvalidSspiNegotiation|セキュリティ サポート プロバイダー インターフェイス ネゴシエーションが失敗しました。|  
|IssuerBindingNotPresentInTokenRequirement|セキュリティ トークン マネージャーでは、セキュリティで保護されたメッセージ交換を記述するトークン要件に、ブートストラップ セキュリティ バインド要素を指定する必要があります。 このトークン要件は、次のように指定されています。|  
|KeyLengthMustBeMultipleOfEight|対称キーについては、指定されたキーの長さが 8 の倍数ではありません。|  
|LsaAuthorityNotContacted|内部 SSL エラーです (詳細については Win32 状態コードを参照してください)。 サーバー証明書がキーの交換に対応しているかどうかを確認してください。|  
|MaximumPolicyRedirectionsExceeded|再帰ポリシー フェッチ制限に達しました。 フェデレーション サービス チェーン内にループがないか確認してください。|  
|MessagePartSpecificationMustBeImmutable|メッセージ部分の指定は、設定する前に固定値にしておく必要があります。|  
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom では、CustomCertificateValidator が必要です。 CustomCertificateValidator プロパティを指定してください。|  
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode.Custom では、CustomUserNamePasswordValidator が必要です。 CustomUserNamePasswordValidator プロパティを指定してください。|  
|MissingMembershipProvider|UserNamePasswordValidationMode.MembershipProvider では、MembershipProvider が必要です。 MembershipProvider プロパティを指定してください。|  
|NoBinaryNegoToSend|相手に送信したバイナリ ネゴシエーションはありません。|  
|NoEncryptionPartsSpecified|指定されたアクションを含むメッセージに、暗号化メッセージ部分が指定されていませんでした。|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|解読トークンの検出に必要な KeyInfo 値が暗号化項目で見つかりませんでした。|  
|NonceLengthTooShort|指定された nonce が短すぎます。 nonce の長さは少なくとも 4 バイト必要です。|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|送信メッセージに対する ID の確認を行うための送信 EndpointAddress がありません。|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|受信応答に対する ID の確認を行うための送信 EndpointAddress がありません。|  
|NoPartsOfMessageMatchedPartsToSign|メッセージの中に、指定されたメッセージ部分仕様に合うものがなかったため、署名は作成されませんでした。|  
|NoPrincipalSpecifiedInAuthorizationContext|承認コンテキストにカスタム プリンシパルが指定されていません。|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|リプレイ検出に必要な nonce を提供するための署名がセキュリティ ヘッダーにありません。|  
|NoSignaturePartsSpecified|指定されたアクションを含むメッセージに、署名メッセージ部分が指定されていませんでした。|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|受信 ID の確認に必要な署名トークンがありません。|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|リプレイ検出の実行に必要なタイムスタンプがセキュリティ ヘッダーにありません。|  
|NoTransportTokenAssertionProvided|セキュリティ ポリシーのエクスポートが失敗しました。 提供された、指定された型のトランスポート トークン アサーションは、sp:TransportBinding セキュリティ ポリシー アサーションを含むトランスポート トークン アサーションを作成していません。|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|共通鍵セキュリティ プロトコルには、共通鍵トークン プロバイダーと共通鍵トークン認証システム、または公開鍵トークン プロバイダーを構成できますが、 両方を構成することはできません。|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|この操作は、受信側のセキュリティ ヘッダーに対しては実行できません。|  
|OperationDoesNotAllowImpersonation|指定された名前と名前空間を持つコントラクトに属する指定されたサービス操作は、偽装を許可していません。|  
|PolicyRequiresConfidentialityWithoutIntegrity|指定されたアクションのメッセージ セキュリティ ポリシーには、整合性が確保されない機密性が必要です。 整合性を確保しない機密性はサポートされていません。|  
|PrimarySignatureIsRequiredToBeEncrypted|プライマリ署名は暗号化されている必要があります。|  
|PropertySettingErrorOnProtocolFactory|指定されたセキュリティ プロトコル ファクトリの必須のプロパティが設定されていないか、このプロパティに無効な値が含まれています。|  
|ProtocolFactoryCouldNotCreateProtocol|このプロトコル ファクトリでプロトコルを作成できません。|  
|PublicKeyNotRSA|公開キーは RSA キーではありません。|  
|RequiredMessagePartNotEncrypted|指定された必須のメッセージ部分が暗号化されていませんでした。|  
|RequiredMessagePartNotEncryptedNs|指定された必須のメッセージ部分が暗号化されていませんでした。|  
|RequiredMessagePartNotSigned|指定された必須のメッセージ部分が署名されていませんでした。|  
|RequiredMessagePartNotSignedNs|指定された必須のメッセージ部分が署名されていませんでした。|  
|RequiredSecurityHeaderElementNotSigned|指定された ID を持つ指定されたセキュリティ ヘッダー要素は署名されている必要があります。|  
|RequiredSecurityTokenNotEncrypted|指定された添付モードの指定されたセキュリティ トークンは暗号化されている必要があります。|  
|RequiredSecurityTokenNotSigned|指定された添付モードの指定されたセキュリティ トークンは署名されている必要があります。|  
|RequiredSignatureMissing|署名はセキュリティ ヘッダーに含まれている必要があります。|  
|RequireNonCookieMode|指定された名前空間を持つ指定されたバインディングは、クッキー セキュリティ コンテキスト トークンを発行するように構成されていますが、 COM+ Integration サービスはクッキー セキュリティ コンテキスト トークンをサポートしていません。|  
|RevertingPrivilegeFailed|指定された例外が発生したため、元に戻す処理に失敗しました。|  
|RSTRAuthenticatorIncorrect|RequestSecurityTokenResponse の CombinedHash が正しくありません。|  
|SecureConversationCancelNotAllowedFaultReason|セキュリティで保護されたメッセージ交換の取り消しは、バインディングによって許可されていません。|  
|SecureConversationDriverVersionDoesNotSupportSession|構成された SecureConversation バージョンはセッションをサポートしていません。 WSSecureConversationFeb2005 以上を使用してください。|  
|SecureConversationRequiredByReliableSession|セキュリティで保護された通信を使用せずに、信頼できるセッションを確立することはできません。 セキュリティで保護されたメッセージ交換を有効にしてください。|  
|SecurityAuditFailToLoadDll|指定されたダイナミック リンク ライブラリ (dll) を読み込むことができませんでした。|  
|SecurityAuditNotSupportedOnChannelFactory|SecurityAuditBehavior は、チャネル ファクトリではサポートされていません。|  
|SecurityAuditPlatformNotSupported|現在のプラットフォームでは、セキュリティ ログへの監査メッセージの書き込みはサポートされていません。 監査メッセージはアプリケーション ログに書き込む必要があります。|  
|SecurityBindingElementCannotBeExpressedInConfig|エンドポイントのセキュリティ ポリシーがインポートされました。 このセキュリティ ポリシーには、Windows Communication Foundation の構成では表現できない要件が含まれています。 生成された構成ファイルで、必須の SecurityBindingElement パラメーターに関するコメントを参照してください。 コードを使用して正しいバインド要素を作成してください。 構成ファイル内のバインド構成はセキュリティで保護されていません。|  
|SecurityBindingSupportsOneWayOnly|指定されたコントラクトに対する指定されたバインディングの SecurityBinding は、OneWay 操作のみをサポートしています。|  
|SecurityContextDoesNotAllowImpersonation|指定されたアクションを含む要求メッセージの UltimateReceiver ロールの SecurityContext が Windows ID に割り当てられていないため、偽装を開始できません。|  
|SecurityListenerClosing|リスナーは、閉じている途中のため、セキュリティで保護された新しいメッセージ交換を受け入れていません。|  
|SecurityListenerClosingFaultReason|サーバーは、閉じている途中のため、現在はセキュリティで保護された新しいメッセージ交換を受け入れていません。 後で再試行してください。|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|この操作が実行される前に、セキュリティ プロトコル ファクトリが設定されている必要があります。|  
|SecuritySessionAbortedFaultReason|セキュリティ セッションが中止されました。 これは、セッションでメッセージが長時間受信されなかったことが原因である可能性があります。|  
|SecuritySessionKeyIsStale|セッション キーを使用してアプリケーション メッセージをセキュリティで保護するには、セッション キーを更新する必要があります。|  
|SecuritySessionLimitReached|セキュリティ セッションを作成できません。 後でやり直してください。|  
|SecuritySessionNotPending|指定された ID を持つ保留中のセキュリティ セッションはありません。|  
|SecurityTokenParametersHasIncompatibleInclusionMode|指定されたバインディングは、互換性のないセキュリティ トークンの指定されたインクルード モードが設定されたセキュリティ トークン パラメーターを使用して構成されています。 別のセキュリティ トークンのインクルード モードを指定してください。|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|指定されたコントラクトの指定されたバインディングは、EncryptedKeys への添付されない参照をサポートしていない、互換性のないセキュリティ バージョンで構成されています。 バインディングのセキュリティ バージョンとして、指定された値以降を使用してください。|  
|SecurityVersionDoesNotSupportSignatureConfirmation|指定された SecurityVersion は署名確認をサポートしていません。 これより後の SecurityVersion を使用してください。|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|指定されたコントラクトの指定されたバインディングは、証明書の拇印値を使用した X.509 トークンへの外部参照をサポートしていないセキュリティ バージョンで構成されています。 バインディングのセキュリティ バージョンとして、指定された値以降を使用してください。|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|セキュリティ トークン パラメーターは、各メッセージのサポート トークンを使用して指定する必要があります。|  
|ServerCertificateNotProvided|受信側が証明書を提供しませんでした。 この証明書は TLS プロトコルによって要求されています。 送信側と受信側の両方とも、各自の証明書にアクセスする必要があります。|  
|SignatureConfirmationNotSupported|構成されている SecurityVersion は署名確認をサポートしていません。 WSSecurityXXX2005 以上を使用してください。|  
|SignatureConfirmationRequiresRequestReply|署名確認を行えるようにするには、プロトコル ファクトリで Request/Reply セキュリティをサポートする必要があります。|  
|SignatureNotExpected|このメッセージに署名は必要ありません。|  
|SigningTokenHasNoKeys|指定された署名トークンにはキーがありません。 このセキュリティ トークンは、暗号化操作を実行するためにセキュリティ トークンを必要とするコンテキストで使用されます。ただし、このトークンには暗号化キーが含まれていません。 このトークンの型が暗号化操作をサポートしていないか、特定のトークン インスタンスに暗号化キーが含まれていません。 構成を確認し、暗号化を無効とするトークンの型 (UserNameSecurityToken など) が、暗号化操作を必要とするコンテキスト (保証サポート トークンなど) で指定されていないことを確認してください。|  
|SpnegoImpersonationLevelCannotBeSetToNone|SSPI は、'None' という偽装レベルをサポートしていません。 Identification、Impersonation または Delegation のいずれかのレベルを指定してください。|  
|SslClientCertMustHavePrivateKey|指定された証明書には秘密キーが必要です。 プロセスには秘密キーへのアクセス権が必要です。|  
|SslServerCertMustDoKeyExchange|指定された証明書には、キー交換に対応した秘密キーが必要です。 プロセスには秘密キーへのアクセス権が必要です。|  
|StandardsManagerCannotWriteObject|このトークン シリアライザーは、指定されたオブジェクトをシリアル化できません。  これがカスタム型である場合は、カスタム シリアライザーを提供する必要があります。|  
|TimeStampHasCreationAheadOfExpiry|このセキュリティ タイムスタンプは、作成時刻が有効期限以降であるため、無効です。|  
|TimeStampHasCreationTimeInFuture|このセキュリティ タイムスタンプは、作成時刻が未来の日付であるため、無効です。 現在の時刻と許可される時刻のずれが指定されています。|  
|TimeStampHasExpiryTimeInPast|このセキュリティ タイムスタンプは、有効期限が過去の日付であるため、古くなっています。 現在の時刻と許可される時刻のずれが指定されています。|  
|TimeStampWasCreatedTooLongAgo|このセキュリティ タイムスタンプは、作成時刻がかなり以前であるため、古くなっています。 現在の時刻、タイムスタンプの最大有効期限、および許可される時刻のずれが指定されています。|  
|TokenProviderCannotGetTokensForTarget|トークン プロバイダーは指定された対象のトークンを取得できません。|  
|TooManyIssuedSecurityTokenParameters|統合されたセキュリティ チェーンの各要素には複数の IssuedSecurityTokenParameters があります。 InfoCard システムは、要素ごとに 1 つの IssuedSecurityTokenParameters しかサポートしていません。|  
|TransportDoesNotProtectMessage|指定されたコントラクトの指定されたバインディングは、トランスポート レベルの整合性と機密性を必要とする認証モードで構成されています。 ただし、トランスポートによって整合性と機密性を実現することはできません。|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 では、X.509 証明書や EncryptedKeys の発行がサポートされません。 WsTrustFeb2005 以上を使用してください。|  
|TrustDriverVersionDoesNotSupportSession|構成されたバージョンの Trust では、セッションがサポートされません。 WSTrustFeb2005 またはそれ以降を使用してください。|  
|UnableToCreateICryptoFromTokenForSignatureVerification|署名確認用の指定されたトークンから ICrypto インターフェイスを作成できません。|  
|UnableToCreateSymmetricAlgorithmFromToken|トークンから指定された対称アルゴリズムを作成できません。|  
|UnableToDeriveKeyFromKeyInfoClause|指定された KeyInfo 句は指定されたトークンに解決されましたが、このトークンには派生に使用できる対称キーが含まれていません。|  
|UnableToFindTokenAuthenticator|指定されたトークンの型に対応するトークン認証システムが見つかりません。 現在のセキュリティ設定により、この型のトークンは承認できません。|  
|UnableToLoadCertificateIdentity|構成で指定された X.509 証明書の ID を読み込めません。|  
|UnexpectedEmptyElementExpectingClaim|指定された名前空間の指定された要素が空であり、有効な ID クレームが指定されていません。|  
|UnknownEncodingInBinarySecurityToken|バイナリ セキュリティ トークンの読み取り中に不明なエンコードが検出されました。|  
|UnsecuredMessageFaultReceived|セキュリティで保護されていないか正しくセキュリティで保護されていないフォールトを相手側から受信しました。 フォールト コードおよび詳細については、内部の FaultException を参照してください。|  
|UnsupportedPasswordType|指定されたユーザー名トークンには、サポートされていないパスワードの種類が含まれています。|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|セキュリティ ポリシーをインポートできません。 セキュリティで保護されたメッセージ交換のブートストラップ バインディングの保護要件はサポートされていません。 セキュリティで保護されたメッセージ交換のブートストラップの保護要件は、要求および応答ともに署名され暗号化されている必要があります。|  
|UnsupportedSecurityPolicyAssertion|指定されたセキュリティ ポリシーのインポート中に、サポートされていないセキュリティ ポリシー アサーションが検出されました。|
