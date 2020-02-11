---
title: Change Data Capture Service für Oracle von Attunity | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a01524acf4fc72cb50732650f1f2e6f58b4ff74d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62771526"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a>Change Data Capture Service für Oracle von Attunity
  Der CDC Service for Oracle ist ein Windows-Dienst, der Oracle-Transaktionsprotokolle scannt und Änderungen an relevanten Oracle-Tabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Änderungstabellen aufzeichnet. Die SQL-Änderungstabellen, in denen die aus Oracle aufgezeichneten Änderungen gespeichert werden, entsprechen vom Typ her den Änderungstabellen, die in der systemeigenen Change Data Capture-Funktion von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden. Dies macht das Verarbeiten dieser Änderungen so einfach wie das Verarbeiten von an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken vorgenommenen Änderungen.  
  
## <a name="installation"></a>Installation  
 Der CDC Service for Oracle kann auf jedem unterstützten Windows-Computer mit Zugriff auf die aufgezeichneten Oracle-Quelldatenbanken und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz installiert werden, auf der sich die CDC-Zieldatenbank befindet. Der CDC Service benötigt keine lokale Installation der Oracle-Datenbank oder der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank, nur die unterstützten Clients. Informationen dazu, wo die erforderlichen Datenbankkomponenten installiert werden müssen, finden Sie in diesem Thema unter **Erforderliche Komponenten für die Datenbank** .  
  
 Bei der Installation des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service for Oracle wird die Benutzeroberfläche der Dienstkonfiguration und das Dienstprogramm am ausgewählten Speicherort abgelegt. Der CDC Service for Oracle wird mithilfe der Oracle CDC Service Configuration Console separat konfiguriert. Weitere Informationen zur Konfiguration des Oracle CDC Service finden Sie unter [Change Data Capture Service für Oracle von Attunity F1 Hilfe](change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 Führen Sie zum Installieren von CDC Service for Oracle **attunityoraclecdcservice. msi** manuell von den SQL Server-Installationsmedien aus. Installationspakete für x86 und x64 befinden sich auf den SQL Server-Installationsmedien unter **.\tools\attunitycdcoracle\\ ** .  
  
 Der CDC Service for Oracle kann auf jedem unterstützten Windows-Computer installiert werden, auf dem der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client installiert ist. Er muss nicht auf dem gleichen Computer installiert sein, auf dem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ziel installiert ist.  
  
## <a name="supported-windows-environments"></a>Unterstützte Windows-Umgebungen  
 Der Change Data Capture Service für Oracle von Attunity kann in den folgenden Windows-Umgebungen ausgeführt werden:  
  
-   Windows 8  
  
-   Windows 7 32 Bit (x86) und 64 Bit (x64)  
  
-   Windows Server 2012  
  
-   Windows Server 2008 R2 mit Service Pack 1  
  
-   Windows Server 2008 32 Bit (x86) und 64 Bit (x64) mit Service Pack 2  
  
## <a name="database-prerequisites"></a>Erforderliche Komponenten für die Datenbank  
 Um den CDC Service for Oracle verwenden zu können, müssen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle-Software installieren. Dies ist eine erforderliche Komponente von Oracle, die vor dem Installieren des Oracle CDC Service vorhanden sein muss. Darüber hinaus müssen Sie den SQL Server-ODBC-Client über das SQL Server-Setup installieren.  
  
 Der CDC Service for Oracle unterstützt die folgenden Versionen:  
  
### <a name="source-oracle-database"></a>Oracle-Quelldatenbank  
  
-   Oracle-Datenbank 11x, alle Versionen  
  
-   Oracle-Datenbank 10x, alle Versionen  
  
### <a name="target-sql-server-database"></a>SQL Server-Zieldatenbank  
 Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="running-the-installation-program"></a>Ausführen des Installationsprogramms  
 Öffnen Sie zum Installieren des CDC Service for Oracle den Installations-Assistenten für die von Ihnen verwendete Windows-Plattform (32/64 Bit), und befolgen Sie die Anleitung auf dem Bildschirm.  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a>Deinstallieren des Change Data Capture Service für Oracle von Attunity  
 Sie deinstallieren den CDC Service for Oracle über die Option Programme und Funktionen in der Systemsteuerung.  
  
 Beim Deinstallieren des CDC Service werden die erstellten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken nicht gelöscht. Zum vollständigen Entfernen des Tools müssen Sie die MSXDBCDC-Datenbank und die jeweiligen CDC-Datenbanken entfernen, die auf der verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Zielinstanz erstellt wurden.  
  
 Wenn Sie die CDC Service-Software auf einem Computer deinstallieren und auf einem anderen Computer installieren, müssen Sie nur die folgenden Definitionen angeben:  
  
-   Dienstkonto  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindungszeichenfolge und -Anmeldeinformationen  
  
-   Masterkennwort  
  
 Alle anderen Definitionen werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert und sind über die vorherige Installation auf einem anderen Computer verfügbar.  
  
## <a name="in-this-documentation"></a>In dieser Dokumentation  
  
-   [Change Data Capture Service für Oracle von Attunity System Architecture](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Oracle CDC Service](the-oracle-cdc-service.md)  
  
-   [Change Data Capture Service für Oracle von Attunity F1 Hilfe](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Change Data Capture Service für Oracle von Attunity – Anleitung](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeiten mit dem Oracle CDC Service](working-with-the-oracle-cdc-service.md)  
  
  
