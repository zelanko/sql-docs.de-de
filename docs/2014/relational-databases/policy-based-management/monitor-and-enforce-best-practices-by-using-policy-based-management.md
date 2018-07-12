---
title: Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 46788407-187e-4b0b-bfe4-529af8d77c60
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0bc95e67c4fc29beb61dc518d2f33b203dcae3fc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240570"
---
# <a name="monitor-and-enforce-best-practices-by-using-policy-based-management"></a>Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung
  Richtlinie der richtlinienbasierten Verwaltung können Sie bewährte Methoden für die Überwachung der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Stellt einer Reihe von Richtliniendateien bereit, importieren Sie als best Practice-Richtlinien, und Auswertung der Richtlinien für einen Zielsatz, der Instanzen, Instanzobjekte, Datenbanken oder Datenbankobjekte enthält. Sie können Richtlinien manuell auswerten, Richtlinien zum Auswerten eines Zielsatzes entsprechend einem Zeitplan festlegen oder Richtlinien zum Auswerten eines Zielsatzes entsprechend einem Ereignis angeben. Weitere Informationen finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](administer-servers-by-using-policy-based-management.md).  
  
## <a name="policy-and-rules-for-database-engine"></a>Richtlinie und Regeln für Datenbank-Engine  
 Die folgende Tabelle enthält die Richtlinien, die mit der Installation von enthaltenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und enthält Informationen über die Regeln zu bewährten Methoden, die einzelnen Richtlinien ausgewertet. Die Richtlinien werden als XML-Dateien gespeichert und werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]importiert. Weitere Informationen über das Importieren von Richtlinien finden Sie unter [Importieren einer Richtlinie der richtlinienbasierten Verwaltung](import-a-policy-based-management-policy.md).  
  
|Richtlinienname|Regel für Best Practice|  
|-----------------|------------------------|  
|Verschlüsselungsalgorithmus für asymmetrischen Schlüssel|[Verschlüsselungsstärke von asymmetrischen Schlüsseln](asymmetric-keys-encryption-strength.md)|  
|Speicherort für Sicherung und Datendatei|[Sicherungsdateien und Datenbankdateien müssen auf separaten Medien gespeichert sein](../../database-engine/backup-files-must-be-on-separate-devices-from-the-database-files.md)|  
|Sicherungs- und Datendateispeicherort|[Platzieren von Daten- und Protokolldateien auf separaten Laufwerken](place-data-and-log-files-on-separate-drives.md)|  
|Automatisches Schließen der Datenbank|[Festlegen der Datenbankoption AUTO_CLOSE auf OFF](set-the-auto-close-database-option-to-off.md)|  
|Automatisches Verkleinern der Datenbank|[Festlegen der AUTO_SHRINK-Datenbankoption auf OFF](set-the-auto-shrink-database-option-to-off.md)|  
|Datenbanksortierung|[Festlegen der Sortierung benutzerdefinierter Datenbanken übereinstimmend zu jener der master- und model-Datenbanken](../../database-engine/set-collation-user-defined-databases-match-master-model-databases.md)|  
|Datenbankseitenüberprüfung|[Festlegen der PAGE_VERIFY-Datenbankoption auf CHECKSUM](set-the-page-verify-database-option-to-checksum.md)|  
|Datenbankseitenstatus|[Prüfen der Integrität von Datenbanken mit fehlerverdächtigen Seiten](check-integrity-of-database-with-suspect-pages.md)|  
|Gastberechtigungen|[Gastberechtigungen für Benutzerdatenbanken](guest-permissions-on-user-databases.md)|  
|Datum der letzten erfolgreichen Sicherung|[Obsolete Sicherung](outdated-backup.md)|  
|Öffentlich – Keine Serverberechtigungen|[Serverberechtigungen für 'public'](server-public-permissions.md)|  
|Überlappung der SQL Server-32-Bit-Affinitätsmaske|[Richtige Affinity Mask und Affinity Input-Output Überlappung](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|Überlappung der SQL Server-64-Bit-Affinitätsmaske|[Richtige Affinity Mask und Affinity Input-Output Überlappung](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|SQL Server-Affinitätsmaske|[Beibehalten des Standardwerts für die Affinitätsmaske](keep-the-affinity-mask-default-value.md)|  
|Schwellenwert für blockierte SQL Server-Prozesse|[Erhöhen oder Deaktivieren des Schwellenwerts für blockierte Prozesse](increase-or-disable-blocked-process-threshold.md)|  
|SQL Server-Standardablaufverfolgung|[Protokolldateien für Standardablaufverfolgung deaktiviert](default-trace-log-files-disabled.md)|  
|SQL Server - Dynamische Sperren|[Beibehalten des Standardwerts für die Konfigurationsoption 'locks'](keep-the-locks-configuration-option-default-value.md)|  
|SQL Server-Lightweightpooling|[Deaktivieren des Lightweightpoolings](disable-lightweight-pooling.md)|  
|SQL Server-Anmeldemodus|[Auswählen eines Authentifizierungsmodus](../security/choose-an-authentication-mode.md)|  
|Maximaler Grad an Parallelität für SQL Server|[Festlegen der 'Max. Grad an Parallelität'-Option auf optimale Leistung](set-the-max-degree-of-parallelism-option-for-optimal-performance.md)|  
|Maximale Arbeitsthreadanzahl von SQL Server für die 32-Bit-Konfiguration von SQL Server 2000|[Überprüfen der Einstellung 'Max. Anzahl von Arbeitsthreads'](verify-max-worker-threads-setting.md)|  
|Maximale Arbeitsthreadanzahl von SQL Server für die 64-Bit-Konfiguration von SQL Server 2000|[Überprüfen der Einstellung 'Max. Anzahl von Arbeitsthreads'](verify-max-worker-threads-setting.md)|  
|Maximale Arbeitsthreadanzahl von SQL Server für SQL Server 2005 und höher|[Überprüfen der Einstellung 'Max. Anzahl von Arbeitsthreads'](verify-max-worker-threads-setting.md)|  
|SQL Server-Netzwerkpaketgröße|[Netzwerkpaketgröße darf 8060 Bytes nicht überschreiten](network-packet-size-should-not-exceed-8060-bytes.md)|  
|SQL Server-Kennwortablauf|[Ablauf des SQL Server-Anmeldekennworts](sql-server-login-password-expiration.md)|  
|SQL Server-Kennwortrichtlinie|[Sicherheit des SQL Server-Anmeldekennworts](sql-server-login-password-strength.md)|  
|Symmetrische Schlüsselverschlüsselung für Benutzerdatenbanken|[Symmetrische Schlüssel für Benutzerdatenbanken](symmetric-keys-on-user-databases.md)|  
|Symmetrischer Schlüssel für master-Datenbank|[Symmetrische Schlüssel für Systemdatenbanken](symmetric-keys-on-system-databases.md)|  
|Symmetrischer Schlüssel für Systemdatenbanken|[Symmetrische Schlüssel für Systemdatenbanken](symmetric-keys-on-system-databases.md)|  
|Vertrauenswürdige Datenbank|[Bit für die Kennzeichnung der Datenbank als vertrauenswürdig](trustworthy-bit.md)|  
|Fehler aufgrund einer Beschädigung einer Cluster-Datenträgerressource im Windows-Ereignisprotokoll|[Erkennen von SCSI-Hostadapterproblemen](detect-scsi-host-adapter-issues.md)|  
|Gerätetreiber-Steuerungsfehler im Windows-Ereignisprotokoll|[Gerätetreiber-Steuerungsfehler](device-driver-control-error.md)|  
|Fehler "Gerät nicht bereit" im Windows-Ereignisprotokoll|[Fehler 'Gerät nicht bereit'](device-not-ready-error.md)|  
|Fehler aufgrund fehlerhafter E/A-Anforderung im Windows-Ereignisprotokoll|[Fehlerhafte Eingabe Ausgabeanforderung erkennen](detect-failed-input-and-output-requests.md)|  
|E/A-Verzögerungswarnung im Windows-Ereignisprotokoll|[Check Disk Input and Output Subsystem for IO Delay Problems (Überprüfen des Datenträger-E/A-Subsystems auf E/A-Verzögerungen)](check-disk-input-and-output-subsystem-for-io-delay-problems.md)|  
|E/A-Fehler im Windows-Ereignisprotokoll während eines Hardwareseitenfehlers|[Input and Output Error During Hard Page Fault (Eingabe- und Ausgabefehler während eines Hardwareseitenfehlers)](input-and-output-error-during-hard-page-fault.md)|  
|Fehler beim erneuten Leseversuch im Windows-Ereignisprotokoll|[Überprüfen des Datenträger-E/A-Subsystems auf Lesewiederholungsprobleme](check-disk-input-output-subsystem-for-read-retry-problems.md)|  
|E/A-Timeoutfehler des Speichersystems im Windows-Ereignisprotokoll|[Speichersystem – E/A-Timeout](storage-system-input-output-time-out.md)|  
|Fehler aufgrund eines Systemfehlers im Windows-Ereignisprotokoll|[Unerwartete Systemfehler](unexpected-system-failures.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Facets der richtlinienbasierten Verwaltung](working-with-policy-based-management-facets.md)  
  
  
