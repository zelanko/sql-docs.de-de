---
title: Speichern und Ausführen von Paketen (SQL Server-Import / Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 43cd7f780bfb85930b1abfb144f65a2f7e7b02a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169252"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>Paket speichern und ausführen (SQL Server-Import/Export-Assistent)
  Verwenden der **Paket speichern und ausführen** Dialogfeld, um das Paket sofort speichern zur späteren Ausführung oder beides ausführen.  
  
> [!NOTE]  
>  Wenn Sie ein Paket vor dem Abschluss der Ausführung beenden, das Paket wird nicht gespeichert, auch wenn Sie die **speichern** Kontrollkästchen.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import / Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen zum Starten des Assistenten als auch die Berechtigungen erforderlich, um den Assistenten erfolgreich ausführen, finden Sie unter [führen Sie die SQL Server-Import / Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **Sofort ausführen**  
 Wählen Sie diese Option aus, um das Paket sofort auszuführen.  
  
 **SSIS-Paket speichern**  
 Speichern Sie das Paket zur späteren Ausführung, mit der Option, es sofort auszuführen.  
  
> [!NOTE]  
>  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], die Möglichkeit, das vom Assistenten erstellte Paket speichern ist nicht verfügbar.  
  
 **SQL Server**  
 Wählen Sie diese Option aus, um das Paket in der `msdb`-Datenbank von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu speichern.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie ausgewählt haben die **SSIS-Paket speichern** Option.  
  
 **File system**  
 Wählen Sie diese Option aus, um das Paket als Datei mit der Erweiterung *.dtsx zu speichern.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie ausgewählt haben die **SSIS-Paket speichern** Option.  
  
 **Paketschutzebene**  
 Wählen Sie eine Schutzebene aus der Liste aus.  
  
 Die Schutzebene bestimmt die Methode, das Kennwort oder den Benutzerschlüssel und den Bereich des Paketschutzes. Der Schutz kann alle Daten oder nur vertrauliche Daten einschließen. Die Anforderungen und Optionen für die Sicherheit von-Paketen finden Sie unter [Zugriffssteuerung für vertrauliche Daten in Paketen](../security/access-control-for-sensitive-data-in-packages.md) und [Sicherheitsübersicht &#40;Integrationsdienste&#41;](../security/security-overview-integration-services.md).  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie ausgewählt haben die **SSIS-Paket speichern** Option.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie festgelegt haben die **Paketschutzebene** Optionen **sensible Daten mit einem Kennwort verschlüsseln** oder **alle Daten mit einem Kennwort verschlüsseln**.  
  
 **Kennwort erneut eingeben**  
 Geben Sie das Kennwort erneut ein.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie festgelegt haben die **Paketschutzebene** Optionen **sensible Daten mit einem Kennwort verschlüsseln** oder **alle Daten mit einem Kennwort verschlüsseln**.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung von Projekten und Paketen](../packages/run-integration-services-ssis-packages.md)   
 [Speichern von Paketen](../save-packages.md)  
  
  
