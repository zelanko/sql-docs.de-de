---
title: Unterstützte .NET Framework Bibliotheken | Microsoft-Dokumentation
description: Wenn die CLR in SQL Server gehostet wird, können Sie mit unterstützten .NET Framework Klassenbibliotheken und nicht unterstützten Bibliotheken erstellen, die Sie bei einer Datenbank registrieren.
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
ms.openlocfilehash: a676688176e164736552460667432919250f8e99
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82261851"
---
# <a name="supported-net-framework-libraries"></a>Unterstützte .NET Framework-Bibliotheken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mit in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gehosteter CLR (Common Language Runtime) können Sie gespeicherte Prozeduren, Trigger, benutzerdefinierte Funktionen, benutzerdefinierte Typen (User-Defined Types, UDT) und benutzerdefinierte Aggregate in verwaltetem Code erstellen. Mit den in den Bibliotheken der .NET Framework-Klasse verfügbaren Funktionen haben Sie Zugriff auf vorgefertigte Klassen, die Funktionen u. a. zur Zeichenfolgenbearbeitung, für erweiterte mathematische Vorgänge, den Dateizugriff und die Kryptografie bereitstellen. Auf diese Klassen können Sie von jeder verwalteten gespeicherten Prozedur, jedem benutzerdefinierten Typ, jedem Trigger, jeder benutzerdefinierten Funktion oder jedem benutzerdefinierten Aggregat aus zugreifen.  
  
> [!NOTE]  
>  Wenn Sie nicht unterstützte Assemblys im globalen Assemblycache (GAC) warten oder aktualisieren, funktioniert die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anwendung möglicherweise nicht mehr. Dies ist darauf zurückzuführen, dass durch das Warten oder Aktualisieren von Bibliotheken im GAC die entsprechenden Assemblys in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht aktualisiert werden. Wenn eine Assembly sowohl in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank als auch im GAC vorhanden ist, müssen die beiden Kopien der Assembly genau übereinstimmen. Stimmen sie nicht überein, tritt ein Fehler auf, wenn die Assembly von der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR-Integration verwendet wird. Wenn Sie Assemblys im GAC warten oder aktualisieren, die auch in der Datenbank registriert sind, einschließlich nicht unterstützter .NET Framework Assemblys, stellen Sie sicher, dass Sie auch die Kopie der Assembly in den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbanken mit der **Alter Assembly** -Anweisung warten oder aktualisieren. Weitere Informationen finden Sie im [Knowledge Base-Artikel 949080](https://support.microsoft.com/kb/949080).  
  
## <a name="supported-libraries"></a>Unterstützte Bibliotheken  
 Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verfügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über eine Liste mit unterstützten .NET Framework-Bibliotheken, die auf Zuverlässigkeits- und Sicherheitsstandards zur Interaktion mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] getestet wurden. Unterstützte Bibliotheken müssen auf dem Server nicht explizit registriert werden, bevor sie in Ihrem Code verwendet werden können. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lädt sie direkt in den globalen Assemblycache (Global Assembly Cache oder GAC).  
  
 Folgende Bibliotheken/Namespaces werden von der CLR-Integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt:  
  
-   CustomMarshalers  
-   Microsoft.VisualBasic  
-   Microsoft.VisualC  
-   mscorlib  
-   System  
-   System.Configuration  
-   System.Core  
-   <legacyBold>System.Data</legacyBold>  
-   System.Data.OracleClient  
-   System.Data.SqlXml  
-   System.Deployment  
-   System.Security  
-   System.Transactions  
-   System.Web.Services  
-   System.Xml  
-   System.Xml.Linq  

<!--
Any modifications to the list above should be duplicated on the following page:
https://docs.microsoft.com/sql/relational-databases/clr-integration/assemblies-designing#supported-net-framework-assemblies
-->

## <a name="unsupported-libraries"></a>Nicht unterstützte Bibliotheken  
 Nicht unterstützte Bibliotheken können Sie nach wie vor von Ihren verwalteten gespeicherten Prozeduren, Triggern, benutzerdefinierten Funktionen, benutzerdefinierten Typen (User-Defined Types, UDT) und benutzerdefinierten Aggregaten aus aufrufen. Die nicht unterstützte Bibliothek muss zunächst [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der **Create Assembly** -Anweisung in der Datenbank registriert werden, bevor Sie in Ihrem Code verwendet werden kann. Alle nicht unterstützten Bibliotheken, die registriert und auf dem Server ausgeführt werden, sollten überprüft und auf Sicherheit und Zuverlässigkeit getestet werden.  
  
 Beispielsweise wird der **System. Director yservices** -Namespace nicht unterstützt. Sie müssen die System. DirectoryServices. dll-Assembly mit **unsicheren** Berechtigungen registrieren, bevor Sie Sie aus Ihrem Code abrufen können. Die **unsichere** Berechtigung ist erforderlich, da Klassen im **System. DirectoryServices** -Namespace die Anforderungen für **Safe** oder **EXTERNAL_ACCESS**nicht erfüllen. Weitere Informationen finden Sie unter [Einschränkungen für das CLR-Integrations Programmiermodell](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md) und [CLR-Integration Code Zugriffssicherheit](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Code Zugriffssicherheit für die CLR-Integration](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Beschränkungen des Programmiermodells für die CLR-Integration](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)  
  
  
