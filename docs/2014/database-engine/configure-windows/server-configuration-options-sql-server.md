---
title: Serverkonfigurationsoptionen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- surface area configuration [SQL Server], sp_configure
- configuration options [SQL Server], when take effect
- server management [SQL Server], configuration options
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], configuring
- configuration options [SQL Server], setting
- options [SQL Server], configuration
- RECONFIGURE statement
- performance [SQL Server], servers
- configuration options [SQL Server]
- RECONFIGURE WITH OVERRIDE statement
- SQL Server, configuring
- sp_configure
- stored procedures [SQL Server], configuration options
- server configuration [SQL Server]
- administering SQL Server, configuration options
ms.assetid: 9f38eba6-39b1-4f1d-ba24-ee4f7e2bc969
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 645aee1374f7dbf3c290500bb35ca47115983670
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640551"
---
# <a name="server-configuration-options-sql-server"></a>Serverkonfigurationsoptionen (SQL Server)
  Sie können die Ressourcen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über Konfigurationsoptionen verwalten und optimieren, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder die gespeicherte Systemprozedur sp_configure verwenden. Die am häufigsten verwendeten Serverkonfigurationsoptionen stehen über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zur Verfügung. Mit sp_configure kann auf alle Konfigurationsoptionen zugegriffen werden. Sie sollten vor dem Festlegen dieser Optionen die Auswirkungen auf Ihr System sorgfältig überdenken. Weitere Informationen finden Sie unter [Anzeigen oder Ändern von Servereigenschaften &#40;SQL Server&#41;](view-or-change-server-properties-sql-server.md).  
  
> [!IMPORTANT]  
>  Erweiterte Optionen sollten ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
## <a name="categories-of-configuration-options"></a>Kategorien von Konfigurationsoptionen  
 Konfigurationsoptionen treten wie folgt in Kraft:  
  
-   Unmittelbar nach dem Festlegen der Option und dem Ausgeben der RECONFIGURE-Anweisung (oder in einigen Fällen der RECONFIGURE WITH OVERRIDE-Anweisung).  
  
     -oder-  
  
-   Nach dem Ausführen der obigen Aktionen und dem Neustarten der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Für Optionen, die einen Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfordern, wird der geänderte Wert zunächst nur in der value-Spalte angezeigt. Nach dem Neustart wird der neue Wert sowohl in der value-Spalte als auch in der value_in_use-Spalte angezeigt.  
  
 Bei einigen Optionen tritt der neue Konfigurationswert erst nach einem Neustart des Servers in Kraft. Wenn Sie den neuen Wert festlegen und sp_configure ausführen, bevor Sie den Server neu starten, wird der neue Wert in der value-Spalte der Konfigurationsoptionen, jedoch nicht in der value_in_use-Spalte angezeigt. Nach dem Neustart des Servers wird der neue Wert in der value_in_use-Spalte angezeigt.  
  
 Selbstkonfigurierende Optionen sind jene Optionen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gemäß den Anforderungen des Systems angepasst werden. In den meisten Fällen ist es dadurch nicht notwendig, die Werte manuell festzulegen. Beispiele dafür sind die Optionen Min. Serverarbeitsspeicher und Max. Serverarbeitsspeicher sowie die Option Benutzerverbindungen.  
  
## <a name="configuration-options-table"></a>Tabelle der Konfigurationsoptionen  
 In der folgenden Tabelle werden alle verfügbaren Konfigurationsoptionen, der Bereich der möglichen Einstellungen und die Standardwerte aufgelistet. Konfigurationsoptionen sind wie folgt mit Buchstabencodes gekennzeichnet:  
  
-   A (Advanced) = Erweiterte Optionen, die nur von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden sollten und das Festlegen von Erweiterte Optionen anzeigen auf 1 erfordern.  
  
-   RR (Restart Required) = Optionen, die den Neustart von [!INCLUDE[ssDE](../../includes/ssde-md.md)] erfordern.  
  
-   SC (Self-Configuring) = Selbstkonfigurierende Optionen.  
  
    |Konfigurationsoption|Mindestwert|Höchstwert|Standard|  
    |--------------------------|-------------------|-------------------|-------------|  
    |[AccessCheckCache-Bucketanzahl](access-check-cache-server-configuration-options.md) (A)|0|16384|0|  
    |[AccessCheckCache-Kontingent](access-check-cache-server-configuration-options.md) (A)|0|2147483647|0|  
    |[Ad Hoc Distributed Queries](ad-hoc-distributed-queries-server-configuration-option.md) (A)|0|1|0|  
    |[Affinity I/O Mask](affinity-input-output-mask-server-configuration-option.md) (A, RR)|-2147483648|2147483647|0|  
    |[Affinity64 I/O Mask](affinity64-input-output-mask-server-configuration-option.md) (A, nur verfügbar in der 64-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])|-2147483648|2147483647|0|  
    |[Affinity Mask](affinity-mask-server-configuration-option.md) (A)|-2147483648|2147483647|0|  
    |[Affinity64 Mask](affinity64-mask-server-configuration-option.md) (A, RR), nur verfügbar in der 64-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|-2147483648|2147483647|0|  
    |[Agent XPs](agent-xps-server-configuration-option.md) (A)|0|1|0<br /><br /> (Wird zu 1 geändert, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent gestartet wird. Der Standardwert ist 0, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beim Setup auf automatischen Start festgelegt wurde.)|  
    |[Allow Updates](allow-updates-server-configuration-option.md) (Veraltet. Darf nicht verwendet werden. Führt beim Neukonfigurieren zu einem Fehler.)|0|1|0|  
    |[Standardeinstellung der Sicherungsprüfsumme](../backup-checksum-default.md)|0|1|0|  
    |[backup compression default](view-or-configure-the-backup-compression-default-server-configuration-option.md)|0|1|0|  
    |[Schwellenwert für blockierte Prozesse](blocked-process-threshold-server-configuration-option.md) (A)|0|86400|0|  
    |[C2-Überwachungsmodus](c2-audit-mode-server-configuration-option.md) (A, RR)|0|1|0|  
    |[clr enabled](clr-enabled-server-configuration-option.md)|0|1|0|  
    |[Common Criteria-Kompatibilität aktiviert](common-criteria-compliance-enabled-server-configuration-option.md) (A, RR)|0|1|0|  
    |[contained database authentication](contained-database-authentication-server-configuration-option.md)|0||0|  
    |[Kostenschwellenwert für Parallelität](configure-the-cost-threshold-for-parallelism-server-configuration-option.md) (A)|0|32767|5|  
    |[cross db ownership chaining](cross-db-ownership-chaining-server-configuration-option.md)|0|1|0|  
    |[Cursorschwellenwert](configure-the-cursor-threshold-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[Erweiterte gespeicherte Prozeduren für Datenbank-E-Mail](database-mail-xps-server-configuration-option.md) (A)|0|1|0|  
    |[Volltext-Standardsprache](configure-the-default-full-text-language-server-configuration-option.md) (A)|0|2147483647|1033|  
    |[default language](configure-the-default-language-server-configuration-option.md)|0|9999|0|  
    |[Standardablaufverfolgung aktiviert](default-trace-enabled-server-configuration-option.md) (A)|0|1|1|  
    |[Ergebnisse von Triggern nicht zulassen](disallow-results-from-triggers-server-configuration-option.md) (A)|0|1|0|  
    |[EKM provider enabled](ekm-provider-enabled-server-configuration-option.md)|0|1|0|  
    |[filestream_access_level](filestream-access-level-server-configuration-option.md)|0|2|0|  
    |[Füllfaktor](configure-the-fill-factor-server-configuration-option.md) (A, RR)|0|100|0|  
    |Maximale Bandbreite für Volltextdurchforstung, siehe [Bandbreite für Volltextdurchforstung](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |Minimale Bandbreite für Volltextdurchforstung, siehe [Bandbreite für Volltextdurchforstung](ft-crawl-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |Maximale Bandbreite für Volltextbenachrichtigung, siehe [Bandbreite für Volltextbenachrichtigung](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|100|  
    |Minimale Bandbreite für Volltextbenachrichtigung, siehe [Bandbreite für Volltextbenachrichtigung](ft-notify-bandwidth-server-configuration-option.md)(A)|0|32767|0|  
    |[Speicher für Indexerstellung](configure-the-index-create-memory-server-configuration-option.md) (A, SC)|704|2147483647|0|  
    |[Lösung für unklare Transaktion](in-doubt-xact-resolution-server-configuration-option.md) (A)|0|2|0|  
    |[Lightweightpooling](lightweight-pooling-server-configuration-option.md) (A, RR)|0|1|0|  
    |[Sperren](configure-the-locks-server-configuration-option.md) (A, RR, SC)|5000|2147483647|0|  
    |[Max. Grad an Parallelität](configure-the-max-degree-of-parallelism-server-configuration-option.md) (A)|0|32767|0|  
    |[Max. Bereich für Volltextdurchforstung](max-full-text-crawl-range-server-configuration-option.md) (A)|0|256|4|  
    |[Max. Serverarbeitsspeicher](server-memory-server-configuration-options.md) (A, SC)|16|2147483647|2147483647|  
    |[max text repl size](configure-the-max-text-repl-size-server-configuration-option.md)|0|2147483647|65536|  
    |[Max. Anzahl von Arbeitsthreads](configure-the-max-worker-threads-server-configuration-option.md) (A)|128|32767<br /><br /> (1024 ist der empfohlene Höchstwert für die 32-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 2048 für die 64-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)|0<br /><br /> 0 konfiguriert automatisch die maximale Anzahl der Arbeitsthreads abhängig von der Anzahl der Prozessoren nach der Formel (256+(*\<Prozessoren>* -4) × 8) für die 32-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und das Doppelte für die 64-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
    |[Medienbeibehaltung](configure-the-media-retention-server-configuration-option.md) (A, RR)|0|365|0|  
    |[Min. Arbeitsspeicher pro Abfrage](configure-the-min-memory-per-query-server-configuration-option.md) (A)|512|2147483647|1024|  
    |[Min. Serverarbeitsspeicher](server-memory-server-configuration-options.md) (A, SC)|0|2147483647|0|  
    |[nested triggers](configure-the-nested-triggers-server-configuration-option.md)|0|1|1|  
    |[Netzwerkpaketgröße](configure-the-network-packet-size-server-configuration-option.md) (A)|512|32767|4096|  
    |[OLE-Automatisierungsprozeduren](ole-automation-procedures-server-configuration-option.md) (A)|0|1|0|  
    |[Geöffnete Objekte](open-objects-server-configuration-option.md) (A, RR, veraltet)|0|2147483647|0|  
    |[Für Ad-hoc-Arbeitsauslastungen optimieren](optimize-for-ad-hoc-workloads-server-configuration-option.md) (A)|0|1|0|  
    |[PH-Timeout](ph-timeout-server-configuration-option.md) (A)|1|3600|60|  
    |[Rang vorausberechnen](precompute-rank-server-configuration-option.md) (A)|0|1|0|  
    |[Prioritätserhöhung](configure-the-priority-boost-server-configuration-option.md) (A, RR)|0|1|0|  
    |[Kostenbeschränkung der Abfragekontrolle](configure-the-query-governor-cost-limit-server-configuration-option.md) (A)|0|2147483647|0|  
    |[Abfragewartezeit](configure-the-query-wait-server-configuration-option.md) (A)|-1|2147483647|-1|  
    |[Wiederherstellungsintervall](configure-the-recovery-interval-server-configuration-option.md) (A, SC)|0|32767|0|  
    |[Remotezugriff](configure-the-remote-access-server-configuration-option.md) (RR)|0|1|1|  
    |[remote admin connections](remote-admin-connections-server-configuration-option.md)|0|1|0|  
    |[remote login timeout](configure-the-remote-login-timeout-server-configuration-option.md)|0|2147483647|10|  
    |[remote proc trans](configure-the-remote-proc-trans-server-configuration-option.md)|0|1|0|  
    |[remote query timeout](configure-the-remote-query-timeout-server-configuration-option.md)|0|2147483647|600|  
    |[Replication XPs (Option)](replication-xps-server-configuration-option.md) (A)|0|1|0|  
    |[Startprozeduren suchen](configure-the-scan-for-startup-procs-server-configuration-option.md) (A, RR)|0|1|0|  
    |[server trigger recursion](server-trigger-recursion-server-configuration-option.md)|0|1|1|  
    |[Festgelegte Workingsetgröße](set-working-set-size-server-configuration-option.md) (A, RR, veraltet)|0|1|0|  
    |[show advanced options](show-advanced-options-server-configuration-option.md)|0|1|0|  
    |[Erweiterte gespeicherte Prozeduren für SMO und DMO](smo-and-dmo-xps-server-configuration-option.md) (A)|0|1|1|  
    |[Füllwörtertransformation](transform-noise-words-server-configuration-option.md) (A)|0|1|0|  
    |[Umstellungsjahr für Angaben mit zwei Ziffern](configure-the-two-digit-year-cutoff-server-configuration-option.md) (A)|1753|9999|2049|  
    |[Benutzerverbindungen](configure-the-user-connections-server-configuration-option.md) (A, RR, SC)|0|32767|0|  
    |[user options](configure-the-user-options-server-configuration-option.md)|0|32767|0|  
    |[xp_cmdshell](xp-cmdshell-server-configuration-option.md) (A)|0|1|0|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
