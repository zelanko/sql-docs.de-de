---
title: Servereigenschaften (Seite „Datenbankeinstellungen“) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.databasesettings.f1
ms.assetid: 1cebdbd3-cbfd-4a02-bba6-a5addf4e3ada
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.custom: ''
ms.date: 05/23/2019
ms.openlocfilehash: bf30a65cf0390c5b8400fe7a390520e4bdb29994
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66771765"
---
# <a name="server-properties---database-settings-page"></a>Servereigenschaften (Seite „Datenbankeinstellungen“)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Auf dieser Seite können Sie Ihre Datenbankeinstellungen anzeigen und ändern.  
  
## <a name="options"></a>enthalten

### <a name="default-index-fill-factor"></a>Standardfüllfaktor für Indizes

Gibt an, bis zu welchem Grad die einzelnen Seiten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gefüllt werden sollen, wenn das Programm mithilfe der vorhandenen Daten einen neuen Index erstellt. Der Füllfaktor wirkt sich auf die Leistung aus, da von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeit für das Teilen von Seiten benötigt wird, wenn diese aufgefüllt werden.
  
Der Standardwert ist 0. Die gültigen Werte liegen zwischen 0 und 100. Bei einem Füllfaktor von 0 bzw. 100 werden gruppierte Indizes mit vollen Datenseiten und nicht gruppierte Indizes mit vollen Blattseiten erstellt; in der obersten Ebene der Indexstruktur wird aber noch Platz gelassen. Die Füllfaktorwerte 0 und 100 sind in jeglicher Hinsicht identisch.
  
Niedrige Werte für den Füllfaktor bewirken, dass von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neue Indizes mit Seiten erstellt werden, die nicht gefüllt sind. Jeder Index belegt mehr Speicherplatz, aber für später einzufügende Einträge ist mehr Platz. Dadurch müssen nicht zwangsläufig die Seiten geteilt werden.
  
### <a name="wait-indefinitely"></a>Unbegrenzt warten

Gibt an, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während des Wartens auf ein neues Sicherungsband nie ein Timeout auftritt.  

### <a name="try-once"></a>Einmal versuchen

Gibt an, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Timeout abläuft, wenn bei Bedarf kein Sicherungsband verfügbar ist.

### <a name="try-for-minutes"></a>Versuchsdauer Minute(n)

Gibt an, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein Timeout erstellt wird, wenn innerhalb des angegebenen Zeitraums kein Sicherungsband verfügbar ist.  

### <a name="default-backup-media-retention-in-days"></a>Standardbeibehaltungsdauer für Sicherungsmedien (in Tagen)

Gibt eine systemweite Standardbeibehaltungsdauer für jedes Sicherungsmedium an, nachdem es für eine Datenbank- oder Transaktionsprotokollsicherung verwendet wurde. Durch die Option wird verhindert, dass Sicherungen vor Ablauf der angegebenen Anzahl von Tagen überschrieben werden.  

#### <a name="compress-backup"></a>Sicherung komprimieren

Gibt in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (oder höhere Versionen) die aktuelle Einstellung der Option **Komprimierungsstandard für Sicherung** an. Durch diese Option wird die Standardeinstellung für die Sicherungskomprimierung auf Serverebene wie folgt festgelegt:

- Wenn das Feld **Sicherung komprimieren** leer ist, werden neue Sicherungen nicht komprimiert.

- Wenn das Kontrollkästchen **Sicherung komprimieren** aktiviert ist, werden neue Sicherungen standardmäßig komprimiert.
  
    > [!IMPORTANT]
    >  Standardmäßig steigt die CPU-Nutzung durch die Komprimierung erheblich, und die bei der Komprimierung zusätzlich verbrauchten CPU-Ressourcen können sich negativ auf gleichzeitige Vorgänge auswirken. Daher ist es u.U. sinnvoll, in einer Sitzung, bei der die CPU-Nutzung durch [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) eingeschränkt ist, komprimierte Sicherungen mit niedriger Priorität zu erstellen. Weitere Informationen finden Sie unter [Einschränken der CPU-Nutzung durch die Sicherungskomprimierung mithilfe der Ressourcenkontrolle &#40;Transact-SQL&#41;](../.. relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).
  
Wenn Sie Mitglied der festen Serverrolle **sysadmin** oder **serveradmin** sind, können Sie die Einstellung durch Klicken auf das Kontrollkästchen **Sicherung komprimieren** ändern.  
  
Informationen finden Sie unter [Anzeigen oder Konfigurieren der Serverkonfigurationsoption „Standardeinstellung für die Sicherungskomprimierung“](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md) und [Sicherungskomprimierung &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).  

#### <a name="backup-checksum"></a>Sicherungsprüfsumme

Mit dieser Option können Sie die Einstellung „sp_configure“ für die *Standardeinstellung der Sicherungsprüfsumme* umschalten. Diese Funktion erleichtert es Ihnen, die Standardeinstellung der Sicherungsprüfsumme zu aktivieren.

### <a name="recovery-interval-minutes"></a>Wiederherstellungsintervall (Minuten)

Legt die maximale Anzahl von Minuten pro Datenbank für die Wiederherstellung von Datenbanken fest. Die Standardeinstellung ist 0; bei dieser Einstellung wird die Option automatisch von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]konfiguriert. In der Praxis bedeutet diese Option eine Wiederherstellungszeit von weniger als einer Minute und das Auftreten eines Prüfpunktes in Abständen von ungefähr einer Minute bei aktiven Datenbanken. Weitere Informationen finden Sie unter [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md).  
  
### <a name="data"></a>data

Gibt den Standardspeicherort für Datendateien an. Klicken Sie auf die Schaltfläche Durchsuchen, um zu einem neuen Standardspeicherort zu navigieren. Wird erst nach dem Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirksam.  
  
### <a name="log"></a>Log
  
Gibt den Standardspeicherort für Protokolldateien an. Klicken Sie auf die Schaltfläche Durchsuchen, um zu einem neuen Standardspeicherort zu navigieren. Wird erst nach dem Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wirksam.  
  
### <a name="configured-values"></a>Konfigurierte Werte

Zeigt für die Optionen in diesem Bereich konfigurierte Werte an. Wenn Sie diese Werte ändern, klicken Sie anschließend auf **Ausgeführte Werte** , um zu sehen, ob die Änderungen wirksam sind. Sind sie nicht wirksam, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zuerst neu gestartet werden.  
  
### <a name="running-values"></a>Ausgeführte Werte

Zeigt die gegenwärtig ausgeführten Werte für die Optionen in diesem Bereich an. Diese Werte sind schreibgeschützt.  
  
## <a name="see-also"></a>Weitere Informationen

- [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)

- [Angeben des Füllfaktors für einen Index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)