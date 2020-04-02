---
title: System-Basistabellen | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system base tables [SQL Server]
- hobt [SQL Server]
- base tables
ms.assetid: 31f2df90-651f-4699-8067-19f59b60904f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ac374b9222f9bd592312f79173859691b495276
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531192"
---
# <a name="system-base-tables"></a>Systembasistabellen
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Systembasistabellen sind die zugrunde liegenden Tabellen, in denen die Metadaten für eine bestimmte Datenbank gespeichert werden. Die **Masterdatenbank** ist in dieser Hinsicht besonders, da sie einige zusätzliche Tabellen enthält, die in keiner der anderen Datenbanken gefunden werden. Diese Tabellen enthalten permanente Metadaten, deren Bereich serverweit ist.  
  
> [!IMPORTANT]  
>  Die Systembasistabellen werden nur in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwendet und dienen nicht der allgemeinen Verwendung durch Kunden. Sie können geändert werden, und ihre Kompatibilität wird nicht garantiert.  
  
## <a name="system-base-table-metadata"></a>Metadaten-Systembasistabelle  
 Ein Grantee, der über die Berechtigung CONTROL, ALTER oder VIEW DEFINITION für eine Datenbank verfügt, kann Systembasistabellenmetadaten in der **Katalogansicht sys.objects** anzeigen. Der Stipendiat kann auch die Namen und Objekt-IDs von Systembasistabellen mithilfe integrierter Funktionen wie [OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md) und [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)auflösen.  
  
 Um eine Bindung zu einer Systembasistabelle herzustellen, muss ein Benutzer eine dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC) zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufbauen. Der Versuch, eine SELECT-Abfrage aus einer Systembasistabelle auszuführen, ohne dass mithilfe von DAC eine Verbindung hergestellt wurde, löst einen Fehler aus.  
  
> [!IMPORTANT]  
>  Zugriff auf Systembasistabellen mithilfe von DAC ist nur für [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Mitarbeiter und nicht für die Verwendung durch Kunden vorgesehen.  
  
## <a name="system-base-tables"></a>Systembasistabellen  
 In der folgenden Tabelle werden die Systembasistabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgeführt und beschrieben.  
  
|Basistabelle|BESCHREIBUNG|  
|----------------|-----------------|  
|**sys.sysschobjs**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt ein Objekt in der Datenbank dar.|  
|**sys.sysschobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Service Broker-Entität in der Datenbank. Service Broker-Entitäten schließen Folgendes ein:<br /><br /> Nachrichtentyp<br /><br /> Dienstvertrag<br /><br /> Dienst<br /><br /> Die Namen und Typen verwenden binäre Sortierung, die nicht geändert wird.|  
|**sys.sysclsobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede klassifizierte Entität, für die die gleichen allgemeinen Eigenschaften gelten, darunter die folgenden:<br /><br /> Assembly<br /><br /> Sicherungsmedium<br /><br /> Volltextkatalog<br /><br /> Partitionsfunktion<br /><br /> Partitionsschema<br /><br /> Dateigruppe<br /><br /> Verbergungsschlüssel|  
|**sys.sysnsobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Namespace-bezogene Entität. Diese Tabelle wird zum Speichern von XML-Auflistungsentitäten verwendet.|  
|**sys.syscolpars**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Spalte in einer Tabelle, Sicht oder Tabellenwertfunktion. Sie enthält auch Zeilen für jeden Parameter einer Prozedur oder einer Funktion.|  
|**sys.systypedsubobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede typisierte untergeordnete Entität. Nur Parameter für Partitionsfunktionen fallen in diese Kategorie.|  
|**sys.sysidxstats**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Index oder Statistiken für Tabellen und indizierte Sichten<br /><br /> Hinweis: Jeder Index (außer Heap) ist einer Statistik zugeordnet, die denselben Namen wie der Index hat.|  
|**sys.sysiscols**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden permanenten Index und jede Statistikspalte.|  
|**sys.sysscalartypes**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden benutzerdefinierten oder Systemtyp.|  
|**sys.sysdbreg**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jede registrierte Datenbank.|  
|**sys.sysxsrvs**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jeden lokalen, Verbindungs- oder Remoteserver.|  
|**sys.sysrmtlgns**|Diese Systembasistabelle ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jede Remoteanmeldungszuordnung. Sie wird für die Zuordnung von eingehenden lokalen Anmeldungen, die vorgeben, von einem entsprechenden Server zu stammen, an eine tatsächliche lokale Anmeldung verwendet.|  
|**sys.syslnklgns**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jede verknüpfte Anmeldungszuordnung. Verknüpfte Anmeldungszuordnungen werden von Remoteprozeduraufrufen und verteilten Abfragen vom lokalen Server zum entsprechenden Verbindungsserver verwendet.|  
|**sys.sysxlgns**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jeden Serverprinzipal.|  
|**sys.sysdbfiles**|Ist in jeder Datenbank vorhanden. Wenn die Spalte **dbid** Null ist, stellt die Zeile eine Datei dar, die zu dieser Datenbank gehört. In der **Masterdatenbank** kann die Spalte **dbid** ungleich Null sein. Wenn dies der Fall ist, steht die Zeile für eine Masterdatei.|  
|**sys.sysusermsg**|Ist nur in der **Masterdatenbank** vorhanden. Jede Zeile stellt eine benutzerdefinierte Fehlermeldung dar.|  
|**sys.sysprivs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Berechtigung auf Datenbank- oder Serverebene.<br /><br /> Hinweis: Berechtigungen auf Serverebene werden in der **Masterdatenbank** gespeichert.|  
|**sys.sysowners**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt einen Datenbankprinzipal dar.|  
|**sys.sysobjkeycrypts**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden symmetrischen Schlüssel, jede Verschlüsselung oder kryptografische Eigenschaft, die einem Objekt zugeordnet ist.|  
|**sys.syscerts**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jedes Zertifikat in einer Datenbank.|  
|**sys.sysasymkeys**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt einen asymmetrischen Schlüssel dar.|  
|**sys.ftinds**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Volltextindex in der Datenbank.|  
|**sys.sysxprops**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede erweiterte Eigenschaft.|  
|**sys.sysallocunits**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Speicherzuordnungseinheit.|  
|**sys.sysrowsets**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jedes Partitionsrowset für einen Index oder einen Heap.|  
|**sys.sysrowsetrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Index eines Rowsetverweises.|  
|**sys.syslogshippers**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jeden Datenbankspiegelungszeugen.|  
|**sys.sysremsvcbinds**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Remotedienstbindung.|  
|**sys.sysconvgroup**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Dienstinstanz von Service Broker.|  
|**sys.sysxmitqueue**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Übertragungswarteschlange von Service Broker.|  
|**sys.sysdesend**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden sendenden Endpunkt einer Service Broker-Konversation.|  
|**sys.sysdercv**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden empfangenden Endpunkt einer Service Broker-Konversation.|  
|**sys.sysendpts**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jeden im Server erstellten Endpunkt.|  
|**sys.syswebmethods**|Ist nur in der **Masterdatenbank** vorhanden. Enthält eine Zeile für jede für einen SOAP-aktivierten HTTP-Endpunkt definierte SOAP-Methode, die auf dem Server erstellt wird.|  
|**sys.sysqnames**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Namespace oder jeden qualifizierten Namen für ein 4-Byte-ID-Token.|  
|**sys.sysxmlcomponent**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt eine XML-Schema-Komponente dar.|  
|**sys.sysxmlfacet**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jedes XML-Facet (Beschränkung) der XML-Typdefinition.|  
|**sys.sysxmlplacement**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede XML-Platzierung für XML-Komponenten.|  
|**sys.syssingleobjrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden allgemeinen N-zu-1-Verweis.|  
|**sys.sysmultiobjrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden allgemeinen N-zu-N-Verweis.|  
|**sys.sysobjvalues**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede allgemeine Werteigenschaft einer Entität.|  
|**sys.sysguidrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden GUID-klassifizierten ID-Verweis.|  
  
## <a name="updating-system-base-tables"></a>Aktualisieren von Systembasistabellen    
Sie können die Daten in den Systemtabellen über die Systemkatalogansichten anzeigen. Um die Metadaten in einer Systembasistabelle zu aktualisieren, verwenden Sie die entsprechende TSQL-Schnittstelle (z. B. DDL-Anweisungen). Sie können Systemtabellen nicht manuell aktualisieren. SQL Server meldet die folgenden Meldungen, wenn Sie direkte Aktualisierungen an Systemtabellen durchführen.

### <a name="a-system-table-is-manually-updated"></a>Eine Systemtabelle wird manuell aktualisiert
Msg 17659: Warnung: <id> Die Systemtabellen-ID <id> wurde direkt in der Datenbank-ID aktualisiert, und die Cache-Kohärenz wurde möglicherweise nicht beibehalten. SQL Server sollte neu gestartet werden.

### <a name="starting-a-database-with-a-system-table-that-was-manually-updated"></a>Starten einer Datenbank mit einer Systemtabelle, die manuell aktualisiert wurde
Msg 3859: Warnung: Der Systemkatalog wurde direkt in der Datenbank-ID 17 aktualisiert, zuletzt bei date_time.

### <a name="executing-the-dbcc_checkdb-command-after-a-system-table-is-manually-updated"></a>Ausführen des DBCC_CHECKDB-Befehls, nachdem eine Systemtabelle manuell aktualisiert wurde
Msg 3859: Warnung: Der Systemkatalog wurde direkt in der Datenbank-ID 17 aktualisiert, zuletzt bei date_time.

Wenn Sie manuelle Aktualisierungen an einer Systemtabelle durchführen und auf ein Problem stoßen, werden Sie möglicherweise aufgefordert, aus einer Sicherung wiederherzustellen oder die Daten aus der betroffenen Datenbank in eine neue Datenbank zu kopieren. Erfahren Sie mehr über Fehlermeldungen zu [Benutzeraktionen](https://docs.microsoft.com/sql/relational-databases/errors-events/mssqlserver-8992-database-engine-error?view=sql-server-ver15#user-action).
