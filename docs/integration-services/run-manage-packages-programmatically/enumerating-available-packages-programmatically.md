---
title: "利用可能なパッケージをプログラムで列挙 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programmatically enumerate packages [SSIS]
- existence testing [Integration Services]
- enumerating packages [Integration Services]
ms.assetid: 254ec7ee-d3ff-4361-8995-46e9b9c4dc95
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4ebdf52b9ec71be3845d0fcdf3053b2168467389
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="enumerating-available-packages-programmatically"></a>プログラムによる使用可能なパッケージの列挙
  <a name="top"></a>作業にプログラムで[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]パッケージ、可能性があるかどうか、個々 のパッケージまたはフォルダーが存在する、確認または保存済みパッケージの読み込みおよび実行に使用できるを列挙します。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。    
    
##  <a name="exists"></a>パッケージまたはフォルダーが存在するかどうかを決定します。    
 保存済みのパッケージの読み込みと実行を行う前に、プログラムによってそのパッケージが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 フォルダーに保存されているパッケージを一覧表示する前に、プログラムによりそのフォルダーが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [ページのトップへ](#top)    
    
##  <a name="listing"></a>使用可能なパッケージの列挙    
 プログラムにより保存済みパッケージの一覧を取得するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A>|    
    
 次のサンプルは、これらのメソッドの使用方法を示すコンソール アプリケーションです。    
    
###  <a name="listing_store"></a>例 (SSIS パッケージ ストア)    
 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerPackageInfos%2A> メソッドを使用して、SSIS パッケージ ストアに保存されているパッケージを一覧表示します。 SSIS パッケージ ストアによって管理される既定のストレージの場所は、ファイル システムおよび MSDB です。 これらの場所の中に、追加の論理フォルダーを作成できます。    
    
```vb    
Imports Microsoft.SqlServer.Dts.Runtime    
    
Module Module1    
    
  Sub Main()    
    
    Dim sqlFolder As String    
    Dim sqlServer As String    
    
    Dim ssisApplication As Application    
    Dim sqlPackages As PackageInfos    
    Dim sqlPackage As PackageInfo    
    
    sqlServer = "."    
    
    ssisApplication = New Application()    
    
    ' Get packages stored in MSDB.    
    sqlFolder = "MSDB"    
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)    
    If sqlPackages.Count > 0 Then    
      Console.WriteLine("Packages stored in MSDB:")    
      For Each sqlPackage In sqlPackages    
        Console.WriteLine(sqlPackage.Name)    
      Next    
      Console.WriteLine()    
    End If    
    
    ' Get packages stored in the File System.    
    sqlFolder = "File System"    
    sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer)    
    If sqlPackages.Count > 0 Then    
      Console.WriteLine("Packages stored in the File System:")    
      For Each sqlPackage In sqlPackages    
        Console.WriteLine(sqlPackage.Name)    
      Next    
    End If    
    
    Console.Read()    
    
  End Sub    
    
End Module    
```    
    
```csharp    
using System;    
using Microsoft.SqlServer.Dts.Runtime;    
    
namespace EnumeratePackagesSSIS_CS    
{    
  class Program    
  {    
    static void Main(string[] args)    
    {    
    
      string sqlFolder;    
      string sqlServer;    
    
      Application ssisApplication;    
      PackageInfos sqlPackages;    
    
      sqlServer = ".";    
    
      ssisApplication = new Application();    
    
      // Get packages stored in MSDB.    
      sqlFolder = "MSDB";    
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);    
      if (sqlPackages.Count > 0)    
      {    
        Console.WriteLine("Packages stored in MSDB:");    
        foreach (PackageInfo sqlPackage in sqlPackages)    
        {    
          Console.WriteLine(sqlPackage.Name);    
        }    
        Console.WriteLine();    
      }    
    
      // Get packages stored in the File System.    
      sqlFolder = "File System";    
      sqlPackages = ssisApplication.GetDtsServerPackageInfos(sqlFolder, sqlServer);    
      if (sqlPackages.Count > 0)    
      {    
        Console.WriteLine("Packages stored in the File System:");    
        foreach (PackageInfo sqlPackage in sqlPackages)    
        {    
          Console.WriteLine(sqlPackage.Name);    
        }    
      }    
    
      Console.Read();    
    
    }    
    
  }    
    
}    
```    
    
 [ページのトップへ](#top)    
    
###  <a name="listing_sql"></a>例 (SQL Server)    
 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageInfos%2A> メソッドを使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインスタンスに保存されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パッケージを一覧表示します。    
    
```vb    
Imports Microsoft.SqlServer.Dts.Runtime    
    
Module Module1    
    
  Sub Main()    
    
    Dim sqlFolder As String    
    Dim sqlServer As String    
    Dim sqlUser As String    
    Dim sqlPassword As String    
    
    Dim ssisApplication As Application    
    Dim sqlPackages As PackageInfos    
    Dim sqlPackage As PackageInfo    
    
    sqlFolder = String.Empty    
    sqlServer = "(local)"    
    sqlUser = String.Empty    
    sqlPassword = String.Empty    
    
    ssisApplication = New Application()    
    
    sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword)    
    
    For Each sqlPackage In sqlPackages    
      Console.WriteLine(sqlPackage.Name)    
    Next    
    
    Console.Read()    
    
  End Sub    
    
End Module    
```    
    
```csharp    
using System;    
using Microsoft.SqlServer.Dts.Runtime;    
    
namespace EnumeratePackagesSql_CS    
{    
  class Program    
  {    
    static void Main(string[] args)    
    {    
    
      string sqlFolder;    
      string sqlServer;    
      string sqlUser;    
      string sqlPassword;    
    
      Application ssisApplication;    
      PackageInfos sqlPackages;    
    
      sqlFolder = String.Empty;    
      sqlServer = "(local)";    
      sqlUser = String.Empty;    
      sqlPassword = String.Empty;    
    
      ssisApplication = new Application();    
    
      sqlPackages = ssisApplication.GetPackageInfos(sqlFolder, sqlServer, sqlUser, sqlPassword);    
    
      foreach (PackageInfo sqlPackage in sqlPackages)    
      {    
        Console.WriteLine(sqlPackage.Name);    
      }    
    
      Console.Read();    
    
    }    
  }    
}    
```    
    
 [ページのトップへ](#top)    
   
## <a name="see-also"></a>参照    
 [パッケージの管理 &#40;SSIS サービス&#41;](../../integration-services/service/package-management-ssis-service.md)    
    
  