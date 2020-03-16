---
title: Azure Active Directory in SSDT
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: jroth
reviewer: ''
ms.custom: seo-lt-2019
ms.date: 10/28/2019
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: ed7bc77b48881351a144ed5d217454518abafcc2
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79286204"
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>Azure Active Directory-Unterstützung in SQL Server Data Tools (SSDT)

[!INCLUDE[appliesto-xx-asdb-asdb-xxx-md.md](../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

SQL Server Data Tools (SSDT) bietet mehrere [Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)-Authentifizierungsmethoden (Azure Active Directory).

Öffnen Sie in Visual Studio den **SQL Server-Objekt-Explorer** (im Menü **Ansicht**), und klicken Sie auf **SQL Server hinzufügen**:

![SSDT-Verbindungsdialogfeld](media/azure-active-directory/interactive.png)

#### <a name="which-azure-sql-products"></a>Welche SQL Azure-Produkte?

In diesem Artikel wird Azure AD für die folgende Liste der *Azure SQL-Produkte* in der [Azure-Cloud](https://azure.microsoft.com/) erläutert:

- Azure SQL-Datenbank
- Azure SQL Data Warehouse

## <a name="active-directory-password-authentication"></a>Active Directory-Kennwortauthentifizierung

*Active Directory-Kennwortauthentifizierung* ist ein Mechanismus für das Herstellen einer Verbindung mit den weiter oben aufgelisteten Azure SQL-Produkten. Der Mechanismus verwendet Identitäten in Azure Active Directory (Azure AD). Verwenden Sie diese Methode zum Herstellen einer Verbindung, wenn:

- Sie bei Windows mit Anmeldeinformationen von einer Domäne angemeldet sind, die nicht mit Azure verbunden ist, oder wenn
- Sie die Azure AD-Authentifizierung mit Azure AD verwenden und diese auf der Anfangs- oder Clientdomäne basiert.

Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL-Datenbank unter Verwendung der Azure Active Directory-Authentifizierung](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).  

## <a name="active-directory-integrated-authentication"></a>Integrierte Active Directory-Authentifizierung

Die *integrierte Active Directory-Authentifizierung* ist ein Mechanismus zum Herstellen einer Verbindung mit Azure SQL-Produkten unter Verwendung von Identitäten in Azure Active Directory (Azure AD). Verwenden Sie diese Verbindungsmethode, wenn Sie bei Windows mit Ihren Azure AD-Anmeldeinformationen aus einer Verbunddomäne angemeldet sind. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL-Datenbank unter Verwendung der Azure Active Directory-Authentifizierung](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

## <a name="active-directory-interactive-authentication"></a>Interaktive Active Directory-Authentifizierung

Die *interaktive Active Directory-Authentifizierung* ist verfügbar, wenn Sie über SSDT eine Verbindung mit den aufgelisteten Azure SQL-Produkten herstellen, jedoch nur mit [.NET Framework 4.7.2](https://docs.microsoft.com/dotnet/api/?view=netframework-4.7.2) oder einer höheren Version.

- [Herunterladen und Installieren für eine beliebige Version von .NET Framework](https://www.microsoft.com/net/download/all)
- [Visual Studio 2017 Version 15.6](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes) oder höher

#### <a name="multi-factor-authentication-mfa"></a>Multi-Factor Authentication (MFA)

Die interaktive Active Directory-Authentifizierung unterstützt eine interaktive Authentifizierung zur Verwendung von Azure Active Directory (AD) Multi-Factor Authentication (MFA) für die Authentifizierung bei den aufgeführten Azure SQL-Produkten. Diese Methode unterstützt native Azure AD-Benutzer, Azure AD-Verbundbenutzer und Gastbenutzer anderer Konten. Zu den anderen Kontotypen zählen:

- Business-to-Business (Azure AD B2B).
- Microsoft-Konten, z.B. @outlook.com, @hotmail.com, @live.com.
- Microsoft-fremde Konten, z.B. @gmail.com.

Wenn die MFA-Methode angegeben wird, muss der **Benutzername** angegeben sein und das Feld **Kennwort** deaktiviert sein. 

#### <a name="password-entry"></a>Kennworteingabe

Wenn Sie sich mit *Interaktive Active Directory-Authentifizierung* authentifizieren, wird ein Authentifizierungsfenster geöffnet, in dem Benutzer ein Kennwort manuell eingeben müssen.

![Anmeldedialogfeld](media/azure-active-directory/sign-in.png)

Die MFA wird von Azure AD über dieses zusätzliche MFA-Popupfenster erzwungen.

> [!NOTE]
> Automatisierte Workflows würden durch die Verwendung der *Interaktiven Active Directory-Authentifizierung* blockiert. Für die Interaktion mit dem Authentifizierungsprozess muss eine Person verfügbar sein, die ein Kennwort manuell eingeben kann.

## <a name="known-issues-and-limitations"></a>Einschränkungen und bekannte Probleme

- Die *interaktive Active Directory-Authentifizierung* wird nur unterstützt, wenn eine Verbindung mit den Azure SQL-Produkten hergestellt wird, die am Anfang dieses Artikels aufgeführt werden. Die Authentifizierung wird für SQL Server (lokal oder auf einem virtuellen Computer) nicht unterstützt.
- Die *interaktive Active Directory-Authentifizierung* wird im Dialogfeld „Verbindung“ im *Server-Explorer* nicht unterstützt. Sie müssen eine Verbindung über SSDT mit dem *SQL Server-Objekt-Explorer* herstellen.
- Die Integration für einmaliges Anmelden mit dem aktuell angemeldeten Visual Studio-Konto wird für SSDT nicht unterstützt.
- Die Datei „SQLPackage.exe“, die während der Installation von Visual Studio im Erweiterungsverzeichnis installiert wurde, ist nicht für die Verwendung von dort aus gedacht. Wechseln Sie für die Verwendung der Datei „SQLPackage.exe“ mit Azure AD zu [https://www.microsoft.com/download/details.aspx?id=55088](https://www.microsoft.com/download/details.aspx?id=55088) 
- Der SSDT-Datenvergleich wird bei der Azure AD-Authentifizierung nicht unterstützt.  


## <a name="see-also"></a>Weitere Informationen  

[Multi-Factor Authentication](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)  
[Azure Active Directory-Authentifizierung mit SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)  
[SSDT MSDN-Forum](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT-Team-Blog](https://blogs.msdn.com/b/ssdt/)  
[DACFx-API-Referenz](https://msdn.microsoft.com/library/dn645454.aspx)  
[Herunterladen von SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
