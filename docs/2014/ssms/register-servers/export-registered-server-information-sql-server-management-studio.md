---
title: Exportieren von Informationen zum registrierten Server (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportregisteredservers.f1
helpviewer_keywords:
- Registered Servers [SQL Server], exporting
- exporting registered server information
- transferring registered server information
ms.assetid: b65e168f-b6bf-489c-b8ad-3b8644acf0b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67a5dce0e92f9d9b90f5af3b6e638112b92d450b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52783722"
---
# <a name="export-registered-server-information-sql-server-management-studio"></a>Exportieren von Informationen zum registrierten Server (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie Informationen zum registrierten Server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]speichern und exportieren und an andere Mitarbeiter oder Server verteilen. Diese Exportfunktion ermöglicht eine konsistente Benutzeroberfläche auf mehreren Computern.  
  
 Durch Exportieren und Reimportieren von Dateien mit registrierten Servern können Sie schnell und einfach mehrere Computer mit denselben Servern konfigurieren. Besonders hilfreich ist dies, wenn Sie eine große Anzahl von Servern über Computer an mehreren Standorten verwalten oder einen weniger erfahrenden Benutzer mit elementaren Verbindungseinstellungen konfigurieren möchten.  
  
> [!NOTE]  
>  Serverregistrierungen, die die SQL Server-Authentifizierung nutzen, speichern die Kennwörter auf Benutzerbasis. Nach dem Export und Reimport der Serverregistrierungen müssen Benutzer beim ersten Herstellen der Verbindung für jeden Server ein Kennwort eingeben. Diese werden in den Listen der registrierten Server gespeichert. Bei Servern, die mit der Windows-Authentifizierung registriert wurden, ist dies nicht erforderlich.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-export-registered-server-information"></a>So exportieren Sie Informationen zum registrierten Server  
  
1.  Klicken Sie unter „Registrierte Server“ mit der rechten Maustaste auf eine Servergruppe, und klicken Sie dann auf **Exportieren**.  
  
    > [!NOTE]  
    >  Sie können einen einzelnen Server, die gesamte Struktur registrierter Server oder eine Teilmenge der Struktur registrierter Server exportieren.  
  
2.  Nehmen Sie im Dialogfeld **Registrierte Server exportieren** die folgenden Einstellungen vor.  
  
     **Servergruppe**  
     Geben Sie die zu exportierende Servergruppe an. Sie können alle registrierten Server, die registrierten Server in einer bestimmten Servergruppe bzw. einzelne registrierte Server in die Exportdatei exportieren. Die Exportfunktion ist rekursiv. Wenn z. B. Servergruppe A die Servergruppe B enthält und Servergruppe B die Servergruppen C und D enthält, werden beim Export von Servergruppe A alle Einträge in A, B, C und D exportiert.  
  
     In der Servergruppe werden nur die Servergruppen der Baumstruktur des aktuellen registrierten Servers angezeigt.  
  
     **Datei exportieren**  
     Geben Sie den Namen der Exportdatei in das Textfeld ein, oder verwenden Sie die Schaltfläche zum Durchsuchen (**...**), um eine Exportdatei auf dem Clientcomputer zu suchen. Wenn Sie eine vorhandene Datei auswählen, werden die Daten der registrierten Server an die Datei angehängt. Verwenden Sie die Erweiterung .regsrvr. Wenn die Informationen zum registrierten Server für andere Benutzer oder einen anderen Computer verfügbar sein sollen, können Sie die Datei im Netzwerk speichern. Andere Benutzer können auf die Datei zugreifen und die Informationen zum registrierten Server vollständig oder teilweise importieren. Wenn Sie eine vorhandene Datei als Exportdatei auswählen, wird der Inhalt der Datei mit den Informationen zum registrierten Server überschrieben.  
  
     **Benutzernamen und Kennwörter nicht in die Exportdatei einschließen**  
     Schließen Sie Benutzernamen vom Export in die Datei aus.  
  
    > [!IMPORTANT]  
    >  Die Exportdateien sind zwar verschlüsselt, der Zugriff auf die Datei sollte dennoch sorgfältig kontrolliert werden, wenn diese Benutzernamen und SQL Server-Authentifizierungskennwörter enthält. Benutzernamen und Kennwörter werden deshalb standardmäßig von der Exportdatei ausgeschlossen.  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren Sie Informationen zum registrierten Server &#40;SQL Server Management Studio&#41; ](import-registered-server-information-sql-server-management-studio.md) [erstellen ein neues registriertes Servers &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)  
  
  
