---
title: IMDEmbeddedData インターフェイス |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 203eae4b3660aaf5d1f2ed3a92ba844e88a518ff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34044386"
---
# <a name="imdembeddeddata-interface"></a>IMDEmbeddedData インターフェイス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  IMDEmbeddedData インターフェイスは、埋め込みの管理に使用するパブリック インターフェイス[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]データベースまたは表形式モデル データベース。 インターフェイスが継承、 **IPersistStream**インターフェイスです。 このインターフェイスでは、次の操作を実行できます。  
  
-   コンテナー ドキュメント内の埋め込みストリームの識別子を取得します。  
  
-   ドキュメントの URL を設定します。  
  
-   埋め込みアプリケーションがホスト環境にあるかどうかを示すフラグを設定します。  
  
-   埋め込みアプリケーションが使用する一時ファイルのパスを設定します。  
  
-   現在の埋め込み操作を取り消します。  
  
-   推定サイズ (バイト単位)、埋め込みオブジェクトを保存するためのストリームを取得します。 継承された**IPersistStream**です。  
  
-   埋め込みデータベースが最後に保存されてから変更されていないことを確認します。 継承された**IPersistStream**です。  
  
-   ローカルまたはインプロセス エンジンに埋め込み型データベースを読み込みます。 継承された**IPersistStream**です。  
  
-   ローカルまたはインプロセス データベースをコンテナー ドキュメント内の埋め込みストリームに保存します。 継承された**IPersistStream**です。  
  
## <a name="reference"></a>リファレンス  
 次のドキュメントを参照する、 **IMDEmbeddedData**インターフェイスで提供されている**msmd.h**ヘッダー ファイルです。  
  
### <a name="source-file-pxoembeddeddataidl"></a>ソース ファイル: PXOEmbeddedData.idl  
  
```  
[  
  local,                            
  object,                           
  uuid(6B6691CF-5453-41c2-ADD9-4F320B7FD421),                       
  pointer_default(unique)           
]  
interface IMDEmbeddedData : IPersistStream  
{  
 [id(1), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in] BOOL in_fIsHosted);  
  
 [id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
  
 [id(3), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
  
 [id(4), helpstring("Set the path used by the embedding application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
  
 [id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
};  
```  
  
### <a name="imdembeddeddatagetstreamidentifier"></a>IMDEmbeddedData::GetStreamIdentifier  
  
```  
HRESULT GetStreamIdentifier (  
    [out, retval] BSTR * out_pbstrStreamId  
    )  
```  
  
#### <a name="description"></a>Description  
 ホスト アプリケーションが使用するコンテナー ドキュメント内の埋め込みストリームの識別子を取得します。  
  
#### <a name="parameters"></a>パラメーター  
 *out_pbstrStreamId*  
 ストリーム識別子の場所を指定します。  
  
#### <a name="return-value"></a>戻り値  
 **S_OK**  
 ストリーム識別子が正常に返されました。  
  
 **S_FALSE**  
 ストリーム識別子がありません。  
  
 **E_FAIL**  
 ストリーム識別子へのアクセス中にエラーが発生しました。  
  
#### <a name="remarks"></a>解説  
 現在の接続に埋め込みデータベースが含まれているかどうかを確認するには、OLE DB 接続プロパティから DBPROP_MSMD_EMBEDDED_DATA プロパティの値を確認してください。  
  
 DBPROP_MSMD_EMBEDDED_DATA は、次のいずれかの値をとります。  
  
|名前|値|定義|  
|----------|-----------|----------------|  
|DBPROPVAL_EMBED_NONE|0x00|使用できる埋め込みデータベースがありません。|  
|DBPROPVAL_EMBED_EMBEDDED|0x01|現在のアプリケーションには埋め込みデータベースが含まれています。|  
|DBPROPVAL_EMBED_LINKED|0x02|埋め込みデータベースはリモート アプリケーション (SharePoint Server など) でホストされています。|  
  
#### <a name="source"></a>ソース  
  
```  
[id(1), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
```  
  
### <a name="imdembeddeddatasetcontainerurl"></a>IMDEmbeddedData::SetContainerURL  
  
```  
HRESULT SetContainerURL (  
    [in] BSTR in_bstrURL  
    )  
```  
  
#### <a name="description"></a>Description  
 埋め込みストリームが含まれているファイルの URL を設定します。  
  
#### <a name="parameters"></a>パラメーター  
 *in_bstrURL*  
 ドキュメントの URL を指定します。  
  
#### <a name="return-value"></a>戻り値  
 **S_OK**  
 コンテナー URL は正常に設定されました。  
  
 **E_FAIL**  
 コンテナー URL の設定中にエラーが発生しました。  
  
#### <a name="source"></a>ソース  
  
```  
[id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
```  
  
### <a name="imdembeddeddatasethosted"></a>IMDEmbeddedData::SetHosted  
  
```  
HRESULT SetHosted (  
    [in] BOOL in_fIsHosted  
    )  
```  
  
#### <a name="description"></a>Description  
 埋め込みアプリケーションがホスト環境にあるかどうかを示すフラグを設定します。  
  
#### <a name="parameters"></a>パラメーター  
 *in_ftHosted*  
 呼び出し元がサービス アプリケーション (IIS など) でホストされている場合は TRUE を返します。  
  
#### <a name="return-value"></a>戻り値  
 **S_OK**  
 フラグは正常に設定されました。  
  
 **E_FAIL**  
 フラグの設定中にエラーが発生しました。  
  
#### <a name="source"></a>ソース  
  
```  
[id(5), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in]  BOOL in_fIsHosted);  
```  
  
### <a name="imdembeddeddatasettempdirpath"></a>IMDEmbeddedData::SetTempDirPath  
  
```  
HRESULT SetTempDirPath (  
    [in] BSTR in_bstrPath  
    )  
```  
  
#### <a name="description"></a>Description  
 埋め込みアプリケーションが使用する一時ファイルのパスを設定します。  
  
#### <a name="parameters"></a>パラメーター  
 *in_bstrPath*  
 ホスト アプリケーションが一時ファイルに使用するパス。  
  
#### <a name="return-value"></a>戻り値  
 **S_OK**  
 一時ファイルのディレクトリは正常に設定されました。  
  
 **E_FAIL**  
 パスの設定中にエラーが発生しました。  
  
#### <a name="source"></a>ソース  
  
```  
[id(4), helpstring("Set the path used by the host application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
```  
  
### <a name="imdembeddeddatacancel"></a>IMDEmbeddedData::Cancel  
  
```  
HRESULT Cancel ( void )  
```  
  
#### <a name="description"></a>Description  
 現在の埋め込みデータベース操作を取り消します。  
  
#### <a name="parameters"></a>パラメーター  
 [なし] :  
  
#### <a name="return-value"></a>戻り値  
 **S_OK**  
 操作が正常に取り消されました。  
  
 **DB_E_CANTCANCEL**  
 現在実行中の取り消し可能な操作はありません。  
  
 **E_FAIL**  
 埋め込み操作の取り消し中にエラーが発生しました。  
  
#### <a name="source"></a>ソース  
  
```  
[id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
```  
  
### <a name="imdembeddeddatagetsizemax-ipersiststreamgetsizemax"></a>IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)  
  
```  
HRESULT GetSizeMax (  
    [out] ULARGE_INTEGER * out_pcbSize  
    )  
```  
  
#### <a name="description"></a>Description  
 ストリームの推定サイズ (バイト単位) を取得し、埋め込みオブジェクトを保存します。 継承された**IPersistStream**です。  
  
#### <a name="parameters"></a>パラメーター  
 *in_bstrPath*  
 埋め込みデータベース イメージの推定サイズ (バイト単位)。  
  
#### <a name="return-value"></a>戻り値  
 **S_OK**  
 サイズは正常に取得されました。  
  
 **E_FAIL**  
 サイズの取得中にエラーが発生しました。  
  
### <a name="imdembeddeddataisdirty-ipersiststreamisdirty"></a>IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)  
  
```  
HRESULT IsDirty ( void )  
```  
  
#### <a name="description"></a>Description  
 埋め込みデータベースが最後に保存されてから変更されたかどうかを確認します。 継承された**IPersistStream**です。  
  
#### <a name="parameters"></a>パラメーター  
 なし  
  
#### <a name="return-values"></a>戻り値  
 **S_OK**  
 データベースは最後に保存されてから変更されました。  
  
 **S_FALSE**  
 データベースは最後に保存されてから変更されていません。  
  
 **E_FAIL**  
 データベース状態の取得中にエラーが発生しました。  
  
### <a name="imdembeddeddataload-ipersiststreamload"></a>IMDEmbeddedData::Load (IPersistStream::Load)  
  
```  
HRESULT Load (   
    [in] IStream * in_pStm   
    )  
```  
  
#### <a name="description"></a>Description  
 埋め込みデータベースをローカルまたはインプロセス エンジンに読み込みます。 継承された**IPersistStream**です。  
  
#### <a name="parameters"></a>パラメーター  
 *in_pStm*  
 埋め込みデータベースを読み込むストリーム インターフェイスを指すポインターです。  
  
#### <a name="return-values"></a>戻り値  
 **S_OK**  
 データベースは正常に読み込まれました。  
  
 **E_OUTOFMEMORY**  
 データベースを読み込むためのメモリが不足しています。  
  
 **E_FAIL**  
 異なるデータベースの読み込み中にエラーが発生しました。 **E_OUTOFMEMORY**です。  
  
### <a name="imdembeddeddatasave-ipersiststreamsave"></a>IMDEmbeddedData::Save (IPersistStream::Save)  
  
```  
HRESULT Save (   
    [in] IStream * in_pStm,  
    [in] BOOL in_fClearDirty  
    )  
```  
  
#### <a name="description"></a>Description  
 ローカルまたはインプロセス データベースをコンテナー ドキュメント内の埋め込みストリームに保存します。 継承された**IPersistStream**です。  
  
#### <a name="parameters"></a>パラメーター  
 *in_pStm*  
 埋め込みデータベースの保存先のストリーム インターフェイスを指すポインターです。  
  
 *in_fClearDirty*  
 この操作の後にダーティ フラグを消去する必要があるかどうかを示すフラグです。  
  
#### <a name="return-values"></a>戻り値  
 **S_OK**  
 データベースは正常に保存されました。  
  
 **STG_E_CANTSAVE**  
 異なるデータベースの保存中にエラーが発生しました。 **STG_E_MEDIUMFULL**です。  
  
 **STG_E_MEDIUMFULL**  
 ストレージ デバイスに空き領域がないため、データベースを保存できませんでした。  
  
  
