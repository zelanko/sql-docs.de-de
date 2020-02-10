---
title: Unterstützte .NET Framework Bibliotheken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c2518404830577839bce3e84c4eac9b76c850cd3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62873773"
---
# <a name="supported-net-framework-libraries"></a>Unterstützte .NET Framework-Bibliotheken
  Mit in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehosteter CLR (Common Language Runtime) können Sie gespeicherte Prozeduren, Trigger, benutzerdefinierte Funktionen, benutzerdefinierte Typen (User-Defined Types, UDT) und benutzerdefinierte Aggregate in verwaltetem Code erstellen. Mit den in den Bibliotheken der .NET Framework-Klasse verfügbaren Funktionen haben Sie Zugriff auf vorgefertigte Klassen, die Funktionen u. a. zur Zeichenfolgenbearbeitung, für erweiterte mathematische Vorgänge, den Dateizugriff und die Kryptografie bereitstellen. Auf diese Klassen können Sie von jeder verwalteten gespeicherten Prozedur, jedem benutzerdefinierten Typ, jedem Trigger, jeder benutzerdefinierten Funktion oder jedem benutzerdefinierten Aggregat aus zugreifen.  
  
> [!NOTE]  
>  Wenn Sie nicht unterstützte Assemblys im globalen Assemblycache (Global Assembly Cache, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]GAC) Dienst oder aktualisieren, können Sie Wenn eine Assembly in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR-Integration vorhanden ist. Wenn Sie im GAC Assemblys warten oder aktualisieren, die auch in der Datenbank registriert sind, müssen Sie auch die Kopie der Assembly in den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken mit der `ALTER ASSEMBLY`-Anweisung warten oder aktualisieren. Dies gilt auch für nicht unterstützte .NET Framework-Assemblys. Weitere Informationen finden Sie im [Knowledge Base-Artikel 949080](https://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Unterstützte Bibliotheken  
 Ab [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] verfügt über eine Liste der unterstützten .NET Framework-Bibliotheken, die getestet wurden, um sicherzustellen, dass Sie die Zuverlässigkeits-und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Sicherheitsstandards für die Interaktion mit der direkten Auslastung aus dem globalen Assemblycache (GAC) erfüllen.  
  
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
  
 Der `System.DirectoryServices`-Namespace wird beispielsweise nicht unterstützt. Sie müssen die System.DirectoryServices.dll-Assembly mit `UNSAFE`-Berechtigungen registrieren, bevor Sie sie vom Code aufrufen können. Die `UNSAFE`-Berechtigung ist erforderlich, da Klassen im `System.DirectoryServices`-Namespace die Anforderungen für `SAFE` oder `EXTERNAL_ACCESS` nicht erfüllen. Weitere Informationen finden Sie unter [Einschränkungen für das CLR-Integrations Programmiermodell](clr-integration-programming-model-restrictions.md) und [CLR-Integration Code Zugriffssicherheit](../security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Assembly](../assemblies/creating-an-assembly.md)   
 [Code Zugriffssicherheit für die CLR-Integration](../security/clr-integration-code-access-security.md)   
 [Beschränkungen des Programmiermodells für die CLR-Integration](clr-integration-programming-model-restrictions.md)  
  
  
