---
title: "ICLRStrongName::StrongNameGetPublicKey メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameGetPublicKey
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b7ace87a5eff5235d85507bda649e55ea18fd93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="8648d-102">ICLRStrongName::StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="8648d-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="8648d-103">公開/秘密キーのペアから公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8648d-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="8648d-104">暗号化サービス プロバイダー (CSP) 内のキー コンテナー名、またはバイトの生のコレクションとして、キーのペアを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8648d-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8648d-105">構文</span><span class="sxs-lookup"><span data-stu-id="8648d-105">Syntax</span></span>  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8648d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8648d-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="8648d-107">[in]公開/秘密キー ペアを格納するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="8648d-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="8648d-108">場合`pbKeyBlob`が null、 `szKeyContainer` CSP 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8648d-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="8648d-109">ここで、 [iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)メソッドは、コンテナーに格納されているキーのペアから公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="8648d-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="8648d-110">場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="8648d-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="8648d-111">キーは、1024 ビットの Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8648d-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="8648d-112">この時点では、その他の種類のキーはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="8648d-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8648d-113">[in]公開/秘密キー ペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8648d-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8648d-114">Win32 によって作成された形式では、このペア`CryptExportKey`関数。</span><span class="sxs-lookup"><span data-stu-id="8648d-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8648d-115">場合`pbKeyBlob`は null、によって指定されたキー コンテナー`szKeyContainer`キー ペアを格納すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="8648d-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8648d-116">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="8648d-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="8648d-117">[out]返される公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="8648d-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="8648d-118">`ppbPublicKeyBlob`パラメーターが、共通言語ランタイムによって割り当てられるし、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="8648d-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="8648d-119">呼び出し元を使用して、メモリを解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8648d-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="8648d-120">[out]返される公開キー BLOB のサイズ。</span><span class="sxs-lookup"><span data-stu-id="8648d-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8648d-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="8648d-121">Return Value</span></span>  
 <span data-ttu-id="8648d-122">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="8648d-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8648d-123">コメント</span><span class="sxs-lookup"><span data-stu-id="8648d-123">Remarks</span></span>  
 <span data-ttu-id="8648d-124">公開キーが含まれている、 [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="8648d-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8648d-125">要件</span><span class="sxs-lookup"><span data-stu-id="8648d-125">Requirements</span></span>  
 <span data-ttu-id="8648d-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8648d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8648d-127">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8648d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8648d-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8648d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8648d-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8648d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8648d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="8648d-130">See Also</span></span>  
 [<span data-ttu-id="8648d-131">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="8648d-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="8648d-132">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="8648d-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="8648d-133">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8648d-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)