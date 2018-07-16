---
title: Unterstützt .NET Framework-Bibliotheken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
caps.latest.revision: 25
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8c50e18862d2c3ca5b5e900c6eccebe6e921ea94
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351032"
---
# <a name="supported-net-framework-libraries"></a>Unterstützte .NET Framework-Bibliotheken
  Mit in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehosteter CLR (Common Language Runtime) können Sie gespeicherte Prozeduren, Trigger, benutzerdefinierte Funktionen, benutzerdefinierte Typen (User-Defined Types, UDT) und benutzerdefinierte Aggregate in verwaltetem Code erstellen. Mit den in den Bibliotheken der .NET Framework-Klasse verfügbaren Funktionen haben Sie Zugriff auf vorgefertigte Klassen, die Funktionen u. a. zur Zeichenfolgenbearbeitung, für erweiterte mathematische Vorgänge, den Dateizugriff und die Kryptografie bereitstellen. Auf diese Klassen können Sie von jeder verwalteten gespeicherten Prozedur, jedem benutzerdefinierten Typ, jedem Trigger, jeder benutzerdefinierten Funktion oder jedem benutzerdefinierten Aggregat aus zugreifen.  
  
> [!NOTE]  
>  Wenn Sie warten oder Aktualisieren der nicht unterstützte Assemblys im globalen Assemblycache (GAC), Ihre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Wenn eine Assembly vorhanden, in ist einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR-Integration. Wenn Sie im GAC Assemblys warten oder aktualisieren, die auch in der Datenbank registriert sind, müssen Sie auch die Kopie der Assembly in den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken mit der `ALTER ASSEMBLY`-Anweisung warten oder aktualisieren. Dies gilt auch für nicht unterstützte .NET Framework-Assemblys. Weitere Informationen finden Sie unter [Knowledge Base-Artikel 949080](http://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Unterstützte Bibliotheken  
 Beginnend mit [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] enthält eine Liste der unterstützten .NET Framework-Bibliotheken, die getestet wurden, um sicherzustellen, dass sie Zuverlässigkeit und Sicherheit für die Interaktion mit den Qualitätsstandards [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lädt sie direkt aus dem globalen Assemblycache (GAC).  
  
 Folgende Bibliotheken/Namespaces werden von der CLR-Integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt:  
  
-   CustomMarshalers  
  
-   Microsoft.VisualBasic  
  
-   Microsoft.VisualC  
  
-   mscorlib  
  
-   System  
  
-   System.Configuration  
  
-   System.Data  
  
-   System.Data.OracleClient  
  
-   System.Data.SqlXml  
  
-   System.Deployment  
  
-   System.Security  
  
-   System.Transactions  
  
-   System.Web.Services  
  
-   System.Xml  
  
-   System.Core.dll  
  
-   System.Xml.Linq.dll  
  
## <a name="unsupported-libraries"></a>Nicht unterstützte Bibliotheken  
 Nicht unterstützte Bibliotheken können Sie nach wie vor von Ihren verwalteten gespeicherten Prozeduren, Triggern, benutzerdefinierten Funktionen, benutzerdefinierten Typen (User-Defined Types, UDT) und benutzerdefinierten Aggregaten aus aufrufen. Die nicht unterstützten Bibliotheken müssen zunächst in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank mit der `CREATE ASSEMBLY`-Anweisung registriert werden, bevor sie in Ihrem Code verwendet werden können. Alle nicht unterstützten Bibliotheken, die registriert und auf dem Server ausgeführt werden, sollten überprüft und auf Sicherheit und Zuverlässigkeit getestet werden.  
  
 Der `System.DirectoryServices`-Namespace wird beispielsweise nicht unterstützt. Sie müssen die System.DirectoryServices.dll-Assembly mit `UNSAFE`-Berechtigungen registrieren, bevor Sie sie vom Code aufrufen können. Die `UNSAFE`-Berechtigung ist erforderlich, da Klassen im `System.DirectoryServices`-Namespace die Anforderungen für `SAFE` oder `EXTERNAL_ACCESS` nicht erfüllen. Weitere Informationen finden Sie unter [CLR-Integration Programmierung Einschränkungen](clr-integration-programming-model-restrictions.md) und [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Assembly](../assemblies/creating-an-assembly.md)   
 [Codezugriffssicherheit für CLR-Integration](../security/clr-integration-code-access-security.md)   
 [CLR-Integration: Beschränkungen des Programmiermodells](clr-integration-programming-model-restrictions.md)  
  
  
