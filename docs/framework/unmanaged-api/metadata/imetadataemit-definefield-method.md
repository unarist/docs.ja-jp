---
title: "IMetaDataEmit::DefineField メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2a544d7e676b71fb00b8fd7a3d871867f7f55626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="f421c-102">IMetaDataEmit::DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="f421c-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="f421c-103">指定したメタデータ シグネチャを持つフィールドの定義を作成し、そのフィールド定義トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f421c-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f421c-104">構文</span><span class="sxs-lookup"><span data-stu-id="f421c-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f421c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f421c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f421c-106">[in]`mdTypeDef`外側のクラスまたはインターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="f421c-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="f421c-107">[in]Unicode でフィールド名です。</span><span class="sxs-lookup"><span data-stu-id="f421c-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="f421c-108">[in]フィールドの属性。</span><span class="sxs-lookup"><span data-stu-id="f421c-108">[in] The field attributes.</span></span> <span data-ttu-id="f421c-109">これは、ビットマスク`CorFieldAttr`値。</span><span class="sxs-lookup"><span data-stu-id="f421c-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f421c-110">[in]BLOB としてフィールド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="f421c-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f421c-111">[in]内のバイト数`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="f421c-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="f421c-112">[in]`ELEMENT_TYPE_`  *\** 定数値にします。</span><span class="sxs-lookup"><span data-stu-id="f421c-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="f421c-113">これは、`CorElementType`値。</span><span class="sxs-lookup"><span data-stu-id="f421c-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="f421c-114">場合は、フィールドの定数値を定義しないを使用して`ELEMENT_TYPE_END`です。</span><span class="sxs-lookup"><span data-stu-id="f421c-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f421c-115">[in]フィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="f421c-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="f421c-116">[in]サイズ (Unicode) 文字の`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="f421c-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="f421c-117">[out]`mdFieldDef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f421c-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f421c-118">要件</span><span class="sxs-lookup"><span data-stu-id="f421c-118">Requirements</span></span>  
 <span data-ttu-id="f421c-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f421c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f421c-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f421c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f421c-121">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f421c-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f421c-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f421c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f421c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f421c-123">See Also</span></span>  
 [<span data-ttu-id="f421c-124">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f421c-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f421c-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f421c-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)