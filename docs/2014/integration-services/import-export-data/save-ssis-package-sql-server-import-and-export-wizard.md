---
title: Speichern von Paketen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.savedtspackage.f1
ms.assetid: 7bf8ac6a-5599-43ab-bf5c-e072c11b85a0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6af26cafd4f8dd9bf874ae7860c4f796bef48ae1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62892763"
---
# <a name="save-ssis-package-sql-server-import-and-export-wizard"></a>SSIS-Paket speichern (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **SSIS-Paket speichern** , [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um ein Integration Services-Paket ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) zu benennen, zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` beschreiben und in der Datenbank oder in einer Datei mit der Erweiterung. DTX zu speichern.  
  
> [!NOTE]  
>  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]ist die Option zum Speichern des vom Assistenten erstellten Pakets nicht verfügbar.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Name**  
 Geben Sie einen eindeutigen Namen für das Paket an.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung für das Paket an. Die bewährte Methode ist hierbei, das Paket zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Spar**  
 Zeigen Sie das Ziel an ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Datei), das zuvor für die Zieldatei angegeben wurde.  
  
## <a name="target-dynamic-options"></a>Dynamische Ziel Optionen  
  
### <a name="target--sql-server"></a>Ziel = SQL Server  
 **Servername**  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ziel ausgewählt haben, geben Sie den Namen des Zielservers ein, oder wählen Sie einen aus.  
  
 **Windows-Authentifizierung verwenden**  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ziel ausgewählt haben, gibt diese Option an, ob die Verbindung mit dem Server mithilfe der integrierten Windows-Authentifizierung hergestellt werden soll. Dies ist die bevorzugte Authentifizierungsmethode.  
  
 **SQL Server Authentifizierung verwenden**  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ziel ausgewählt haben, gibt diese Option an, ob die Verbindung mit dem Server mithilfe der SQL Server-Authentifizierung hergestellt werden soll.  
  
 **Benutzername**  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ziel ausgewählt und die SQL-Authentifizierung angegeben haben, geben Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Benutzernamen ein.  
  
 **Kennwort**  
 Wenn Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Ziel ausgewählt und die SQL-Authentifizierung angegeben haben, geben Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Kennwort ein.  
  
### <a name="target--file-system"></a>Ziel = Dateisystem  
 **Dateiname**  
 Wenn Sie ein Dateiziel ausgewählt haben, geben Sie den Pfad für die Zieldatei ein, oder verwenden Sie die Schaltfläche **Durchsuchen** .  
  
 **Durchsuchen**  
 Wenn Sie ein Dateiziel ausgewählt haben, navigieren Sie zur Zieldatei, indem Sie das Dialogfeld **Paket speichern** verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speichern von Paketen](../save-packages.md)  
  
  
