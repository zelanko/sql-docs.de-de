---
title: Paket speichern und ausführen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.saveschedule.f1
ms.assetid: b582c462-3d7a-4a4c-a2a2-2c79fedab75a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c3b1be3f11e3a53ad291ff774cc72468af0d66ca
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966212"
---
# <a name="save-and-execute-package-sql-server-import-and-export-wizard"></a>Paket speichern und ausführen (SQL Server-Import/Export-Assistent)
  Verwenden Sie das Dialogfeld **Paket speichern und ausführen** , um das Paket sofort auszuführen, es zur späteren Ausführung zu speichern oder beides.  
  
> [!NOTE]  
>   Wenn Sie ein Paket vor dem Abschluss der Ausführung beenden, wird das Paket nicht gespeichert, auch wenn Sie das Kontrollkästchen **Speichern** aktiviert haben.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **Sofort ausführen**  
 Wählen Sie diese Option aus, um das Paket sofort auszuführen.  
  
 **SSIS-Paket speichern**  
 Speichern Sie das Paket zur späteren Ausführung, mit der Option, es sofort auszuführen.  
  
> [!NOTE]  
>  In [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] ist die Option zum Speichern des vom Assistenten erstellten Pakets nicht verfügbar.  
  
 **SQL Server**  
 Wählen Sie diese Option aus, um das Paket in der Datenbank zu speichern [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `msdb` .  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie die Option **SSIS-Paket speichern** ausgewählt haben.  
  
 **Dateisystem**  
 Wählen Sie diese Option aus, um das Paket als Datei mit der Erweiterung *.dtsx zu speichern.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie die Option **SSIS-Paket speichern** ausgewählt haben.  
  
 **Paketschutzebene**  
 Wählen Sie eine Schutzebene aus der Liste aus.  
  
 Die Schutzebene bestimmt die Methode, das Kennwort oder den Benutzerschlüssel und den Bereich des Paketschutzes. Der Schutz kann alle Daten oder nur vertrauliche Daten einschließen. Informationen zu den Anforderungen und Optionen für die Paket Sicherheit finden Sie unter [Access Control für sensible Daten in Paketen](../security/access-control-for-sensitive-data-in-packages.md) und [Sicherheitsübersicht &#40;Integration Services&#41;](../security/security-overview-integration-services.md).  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie die Option **SSIS-Paket speichern** ausgewählt haben.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie die Option **Paket Schutz Ebene** auf entweder vertrauliche **Daten mit Kennwort verschlüsseln** oder **alle Daten mit einem Kennwort verschlüsseln**festgelegt haben.  
  
 **Kennwort erneut eingeben**  
 Geben Sie das Kennwort erneut ein.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn Sie die Option **Paket Schutz Ebene** auf entweder vertrauliche **Daten mit Kennwort verschlüsseln** oder **alle Daten mit einem Kennwort verschlüsseln**festgelegt haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführung von Projekten und Paketen](../packages/run-integration-services-ssis-packages.md)   
 [Speichern von Paketen](../save-packages.md)  
  
  
