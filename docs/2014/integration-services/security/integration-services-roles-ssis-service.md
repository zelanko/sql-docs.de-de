---
title: Integration Services-Rollen (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], roles
- db_ssisoperator role
- db_ssisadmin role
- fixed database roles [Integration Services]
- packages [Integration Services], security
- roles [Integration Services]
- db_ssisltduser role
ms.assetid: 9702e90c-fada-4978-a473-1b1423017d80
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9c6f7ef38c779b07b9cbeffc2b9300360620e350
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792870"
---
# <a name="integration-services-roles-ssis-service"></a>Integration Services-Rollen (SSIS-Dienst)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enthält die drei festen Datenbankebene Rollen `db_ssisadmin`, **Db_ssisltduser**, und **Db_ssisoperator**, für das Steuern des Paketzugriffs. Rollen können implementiert werden, nur für Pakete, die gespeichert werden die `msdb` Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Rollen weisen Sie mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zu. Die rollenzuweisungen werden gespeichert, um die `msdb` Datenbank.  
  
## <a name="read-and-write-actions"></a>Lese- und Schreibaktionen  
 In der folgenden Tabelle werden die Lese- und Schreibaktionen von Windows und der festen Rollen auf Datenbankebene in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]beschrieben.  
  
|Rolle|Leseaktion|Schreibaktion|  
|----------|-----------------|------------------|  
|`db_ssisadmin`<br /><br /> oder<br /><br /> `sysadmin`|Eigene Pakete aufzählen.<br /><br /> Alle Pakete aufzählen.<br /><br /> Eigene Pakete anzeigen.<br /><br /> Alle Pakete anzeigen.<br /><br /> Eigene Pakete ausführen.<br /><br /> Alle Pakete ausführen.<br /><br /> Eigene Pakete exportieren.<br /><br /> Alle Pakete exportieren.<br /><br /> Alle Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführen.|Pakete importieren.<br /><br /> Eigene Pakete löschen.<br /><br /> Alle Pakete löschen.<br /><br /> Eigene Paketrollen ändern.<br /><br /> Alle Paketrollen ändern.<br /><br /> <br /><br /> **\*\* Wichtige \* \***  Mitglieder der Db_ssisadmin-Rolle und der Dc_admin-Rolle können in der Lage, ihre Berechtigungen auf Sysadmin erhöhen. Diese Ausweitung von Berechtigungen ist möglich, da diese Rollen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete ändern können und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des sysadmin-Sicherheitskontexts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausgeführt werden können. Konfigurieren Sie als Schutz vor dieser Ausweitung von Berechtigungen beim Ausführen von Wartungsplänen, Datensammlungssätzen und anderen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, die Pakete ausführen, für die Verwendung eines Proxykontos mit einschränkten Berechtigungen, oder fügen Sie der db_ssisadmin-Rolle und der dc_admin-Rolle nur sysadmin-Mitglieder hinzu.|  
|**db_ssisltduser**|Eigene Pakete aufzählen.<br /><br /> Alle Pakete aufzählen.<br /><br /> Eigene Pakete anzeigen.<br /><br /> Eigene Pakete ausführen.<br /><br /> Eigene Pakete exportieren.|Pakete importieren.<br /><br /> Eigene Pakete löschen.<br /><br /> Eigene Paketrollen ändern.|  
|**db_ssisoperator**|Alle Pakete aufzählen.<br /><br /> Alle Pakete anzeigen.<br /><br /> Alle Pakete ausführen.<br /><br /> Alle Pakete exportieren.<br /><br /> Alle Pakete in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausführen.|None|  
|**Windows-Administratoren**|Ausführungsdetails zu allen ausgeführten Paketen anzeigen.|Alle derzeit ausgeführten Pakete anhalten.|  
  
## <a name="sysssispackages-table"></a>Sysssispackages-Tabelle  
 Die **"sysssispackages"** -Tabelle `msdb` enthält die Pakete, die gespeichert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql).  
  
 Die **sysssispackages**-Tabelle enthält Spalten, die Informationen über die Rollen enthalten, die Paketen zugewiesen sind.  
  
-   In der Spalte **readerrole** wird die Rolle angegeben, die über Lesezugriff auf das Paket verfügt.  
  
-   In der Spalte **writerrole** wird die Rolle angegeben, die über Schreibzugriff auf das Paket verfügt.  
  
-   Die **ownersid** -Spalte enthält den eindeutigen Sicherheitsbezeichner des Benutzers, der das Paket erstellte. In dieser Spalte wird der Besitzer des Pakets definiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig werden die Berechtigungen der `db_ssisadmin` und **Db_ssisoperator** festen Rollen auf Datenbankebene und den eindeutigen Sicherheitsbezeichner des Benutzers, der das Paket erstellt hat, gelten für die Leserolle für Pakete und die Berechtigungen des die `db_ssisadmin` -Rolle und die eindeutige Sicherheits-ID des Benutzers, der das Paket erstellt hat gelten für die schreibrolle. Ein Benutzer muss ein Mitglied der `db_ssisadmin`, **Db_ssisltduser**, oder **Db_ssisoperator** Rolle, Lesezugriff auf das Paket verfügen. Ein Benutzer muss ein Mitglied der `db_ssisadmin` Rolle über Schreibzugriff verfügen.  
  
## <a name="access-to-packages"></a>Zugriff auf Pakete  
 Die festen Rollen auf Datenbankebene arbeiten mit benutzerdefinierten Rollen zusammen. Die benutzerdefinierten Rollen sind die Rollen, die Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellen und dann zum Zuweisen von Berechtigungen zu Paketen verwenden. Um auf ein Paket zuzugreifen, muss ein Benutzer Mitglied der benutzerdefinierten Rolle und der entsprechenden festen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datenbankrolle sein. Wenn Benutzer Mitglieder von sind z. B. die **AuditUsers** einer benutzerdefinierten Rolle, die einem Paket zugewiesen ist, sie müssen außerdem Mitglied `db_ssisadmin`, **Db_ssisltduser**, oder **Db_ Ssisoperator** Rolle, Lesezugriff auf das Paket verfügen.  
  
 Wenn Sie Paketen keine benutzerdefinierten Rollen zuweisen, wird der Paketzugriff durch die festen Rollen auf Datenbankebene bestimmt.  
  
 Wenn Sie benutzerdefinierte Rollen verwenden möchten, müssen Sie hinzufügen, damit die `msdb` Datenbank, bevor Sie sie Paketen zuweisen können. Neue Datenbankrollen können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen.  
  
 Die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Rollen auf Datenbankebene gewähren den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Systemtabellen in der msdb-Datenbank Rechte.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (der MSSQLSERVER-Dienst) muss gestartet werden, bevor Sie mit der Datenbank-Engine und den Zugriff verbinden können die `msdb` Datenbank.  
  
 Um Rollen Paketen zuzuweisen, müssen Sie die folgenden Tasks ausführen.  
  
-   **Öffnen Sie den Objekt-Explorer und stellen Sie eine Verbindung mit Integration Services her.**  
  
     Bevor Sie Paketen Rollen mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zuweisen können, müssen Sie den Objekt-Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] öffnen und eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen.  
  
     Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst muss gestartet werden, bevor Sie eine Verbindung mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]herstellen können.  
  
-   **Paketen Lese- und Schreibrollen zuweisen**  
  
     Sie können jedem Paket eine Lese- und eine Schreibrolle zuweisen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Zuweisen einer Lese- und Schreibrolle zu einem Paket](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Erstellen einer benutzerdefinierten Rolle](../create-a-user-defined-role.md)  
  
-   [Herstellen einer Verbindung mit Integration Services](../connect-to-integration-services.md)  
  
  
