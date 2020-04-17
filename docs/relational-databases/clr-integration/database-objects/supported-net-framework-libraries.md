---
title: Unterstützte .NET Framework-Bibliotheken | Microsoft Docs
description: Mit der in SQL Server gehosteten CLR können Sie mithilfe unterstützter .NET Framework-Klassenbibliotheken und nicht unterstützter Bibliotheken erstellen, die Sie bei einer Datenbank registrieren.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 459cd091043d567b4c93555c271213d066f3989e
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487105"
---
# <a name="supported-net-framework-libraries"></a>Unterstützte .NET Framework-Bibliotheken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mit in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehosteter CLR (Common Language Runtime) können Sie gespeicherte Prozeduren, Trigger, benutzerdefinierte Funktionen, benutzerdefinierte Typen (User-Defined Types, UDT) und benutzerdefinierte Aggregate in verwaltetem Code erstellen. Mit den in den Bibliotheken der .NET Framework-Klasse verfügbaren Funktionen haben Sie Zugriff auf vorgefertigte Klassen, die Funktionen u. a. zur Zeichenfolgenbearbeitung, für erweiterte mathematische Vorgänge, den Dateizugriff und die Kryptografie bereitstellen. Auf diese Klassen können Sie von jeder verwalteten gespeicherten Prozedur, jedem benutzerdefinierten Typ, jedem Trigger, jeder benutzerdefinierten Funktion oder jedem benutzerdefinierten Aggregat aus zugreifen.  
  
> [!NOTE]  
>  Wenn Sie nicht unterstützte Assemblys im globalen Assemblycache (GAC) warten oder aktualisieren, funktioniert die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anwendung möglicherweise nicht mehr. Dies ist darauf zurückzuführen, dass durch das Warten oder Aktualisieren von Bibliotheken im GAC die entsprechenden Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht aktualisiert werden. Wenn eine Assembly sowohl in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank als auch im GAC vorhanden ist, müssen die beiden Kopien der Assembly genau übereinstimmen. Stimmen sie nicht überein, tritt ein Fehler auf, wenn die Assembly von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR-Integration verwendet wird. Wenn Sie Assemblys im GAC warten oder aktualisieren, die ebenfalls in der Datenbank registriert sind, einschließlich nicht unterstützter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET Framework-Assemblys, stellen Sie sicher, dass sie auch die Kopie der Assembly in Ihren Datenbanken mit der **ALTER ASSEMBLY-Anweisung** warten oder aktualisieren. Weitere Informationen finden Sie im [Knowledge Base-Artikel 949080](https://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Unterstützte Bibliotheken  
 Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verfügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über eine Liste mit unterstützten .NET Framework-Bibliotheken, die auf Zuverlässigkeits- und Sicherheitsstandards zur Interaktion mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] getestet wurden. Unterstützte Bibliotheken müssen auf dem Server nicht explizit registriert werden, bevor sie in Ihrem Code verwendet werden können. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lädt sie direkt in den globalen Assemblycache (Global Assembly Cache oder GAC).  
  
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
 Nicht unterstützte Bibliotheken können Sie nach wie vor von Ihren verwalteten gespeicherten Prozeduren, Triggern, benutzerdefinierten Funktionen, benutzerdefinierten Typen (User-Defined Types, UDT) und benutzerdefinierten Aggregaten aus aufrufen. Die nicht unterstützte Bibliothek muss [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuerst in der Datenbank unter Verwendung der **CREATE ASSEMBLY-Anweisung** registriert werden, bevor sie in Ihrem Code verwendet werden kann. Alle nicht unterstützten Bibliotheken, die registriert und auf dem Server ausgeführt werden, sollten überprüft und auf Sicherheit und Zuverlässigkeit getestet werden.  
  
 Der **Namespace System.DirectoryServices** wird z. B. nicht unterstützt. Sie müssen die System.DirectoryServices.dll-Assembly mit **UNSAFE-Berechtigungen** registrieren, bevor Sie sie über Ihren Code aufrufen können. Die **UNSAFE-Berechtigung** ist erforderlich, da Klassen im **System.DirectoryServices-Namespace** die Anforderungen für **SAFE** oder **EXTERNAL_ACCESS**nicht erfüllen. Weitere Informationen finden Sie unter [CLR Integration Programming Model Restrictions](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) and [CLR Integration Code Access Security](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [CLR-Integrationscodezugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Beschränkungen des Programmiermodells für die CLR-Integration](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
