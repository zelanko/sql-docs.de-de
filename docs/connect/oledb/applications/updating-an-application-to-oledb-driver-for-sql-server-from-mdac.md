---
title: Aktualisieren einer Anwendung auf den OLE DB-Treiber für SQL Server über MDAC | Microsoft-Dokumentation
description: Aktualisieren einer Anwendung auf den OLE DB-Treiber für SQL Server über MDAC
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, vs. MDAC
- OLE DB Driver for SQL Server, vs. MDAC
- data access [OLE DB Driver for SQL Server], vs. MDAC
- OLE DB Driver for SQL Server, updating applications
author: pmasl
ms.author: pelopes
ms.openlocfilehash: ad36a17367b14a48810d83137b2887eaa75f6ef1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989260"
---
# <a name="updating-an-application-to-ole-db-driver-for-sql-server-from-mdac"></a>Aktualisieren einer Anwendung auf den OLE DB-Treiber für SQL Server über MDAC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Es gibt eine Reihe von Unterschieden zwischen dem OLE DB-Treiber für SQL Server und Microsoft Data Access Components (MDAC). Ab Windows Vista werden die Datenzugriffskomponenten als Windows Data Access Components oder Windows DAC bezeichnet. Zwar stellen beide Technologien nativen Datenzugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken bereit, der OLE DB-Treiber für SQL Server wurde jedoch speziell für die Verwendung der neuen Features von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] entwickelt und bietet gleichzeitig Abwärtskompatibilität mit früheren Versionen.   

 Obwohl MDAC Komponenten zur Verwendung von OLE DB, ODBC und ActiveX Data Objects (ADO) enthält, implementiert der OLE DB-Treiber für SQL Server nur OLE DB (ADO hat allerdings Zugriff auf die Funktionen des OLE DB-Treibers für SQL Server).  

 Der OLE DB-Treiber für SQL Server und MDAC unterscheiden sich in anderen Bereichen wie folgt:  

-   Benutzern, die mit ADO auf den OLE DB-Treiber für SQL Server zugreifen, stehen möglicherweise weniger Filterfunktionen zur Verfügung als bei Zugriff auf den SQL OLE DB-Anbieter.  

-   Wenn eine ADO-Anwendung den OLE DB-Treiber für SQL Server verwendet und versucht, eine berechnete Spalte zu aktualisieren, wird ein Fehler gemeldet. In MDAC wurde das Update zwar akzeptiert, jedoch ignoriert.  

-   Der OLE DB-Treiber für SQL Server ist eine einzelne, eigenständige Dynamic Link Library-Datei (DLL). Die öffentlich verfügbaren Schnittstellen wurden auf ein Minimum reduziert, um sowohl die Verteilung zu erleichtern als auch die Sicherheitsrisiken einzuschränken.  

-   Es werden nur OLE DB-Schnittstellen unterstützt.  

-   Die Namen des OLE DB-Treibers für SQL Server unterscheiden sich von den Namen, die mit MDAC verwendet werden.  

-   Mit dem OLE DB-Treiber für SQL Server sind von MDAC-Komponenten bereitgestellte Benutzerzugriffsfunktionen verfügbar. Dazu gehören u. a.: Verbindungspooling, ADO-Unterstützung und Clientcursorunterstützung. Wenn eine dieser Funktionen verwendet wird, stellt der OLE DB-Treiber für SQL Server nur Datenbankkonnektivität zur Verfügung. MDAC stellt Funktionen wie Ablaufverfolgung, Verwaltungssteuerelemente und Leistungsindikatoren bereit.  

-   Anwendungen können die OLE DB-Basisdienste mit dem OLE DB-Treiber für SQL Server verwenden. Bei Verwendung der OLE DB-Cursor-Engine sollten sie jedoch die Datentyp-Kompatibilitätsoption verwenden, um potenzielle Probleme zu vermeiden, die auftreten können, da die Cursor-Engine die neuen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Datentypen nicht erkennt.  

-   Der OLE DB-Treiber für SQL Server unterstützt den Zugriff auf vorherige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken.  

-   Der OLE DB-Treiber für SQL Server enthält keine XML-Integration. Der OLE DB-Treiber für SQL Server unterstützt „SELECT ... FOR“-XML-Abfragen, jedoch keine anderen XML-Funktionen. Der OLE DB-Treiber für SQL Server unterstützt jedoch den in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten **XML**-Datentyp.  

-   Der OLE DB-Treiber für SQL Server unterstützt das Konfigurieren clientseitiger Netzwerkbibliotheken nur mithilfe von Verbindungszeichenfolgenattributen. Wenn Sie eine umfassendere Netzwerkbibliothekskonfiguration benötigen, müssen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager verwenden.  

-   Bei MDAC-Verbindungszeichenfolgen ist für das **Trusted_Connection**-Schlüsselwort ein boolescher Wert (**true**) zulässig. Eine Verbindungszeichenfolge des OLE DB-Treibers für SQL Server muss **yes** oder **no** verwenden.  

-   An Warnungen und Fehlern wurden geringfügige Änderungen vorgenommen. Vom Server zurückgegebene Warnungen und Fehler behalten bei Übergabe an den OLE DB-Treiber für SQL Server den gleichen Schweregrad bei. Sie sollten sicherstellen, dass die Anwendung gründlich getestet wurde, wenn Sie auf das Abfangen bestimmter Warnungen und Fehler angewiesen sind.  

-   Der OLE DB-Treiber für SQL Server enthält eine strengere Fehlerprüfung als MDAC. Dies bedeutet, dass einige Anwendungen, die den OLE DB-Spezifikationen nicht hundertprozentig entsprechen, sich anders verhalten. Der SQLOLEDB-Anbieter hat beispielsweise die Regel, dass Parameternamen für Ergebnisparameter mit „\@“ beginnen müssen, nicht erzwungen, der OLE DB-Treiber für SQL Server jedoch schon.  

-   Der OLE DB-Treiber für SQL Server verhält sich anders als MDAC, wenn bei Verbindungen ein Fehler auftritt. MDAC gibt beispielsweise zwischengespeicherte Eigenschaftswerte für eine fehlgeschlagene Verbindung zurück, während der OLE DB-Treiber für SQL Server einen Fehler an die aufrufende Anwendung meldet.  

-   Der OLE DB-Treiber für SQL Server generiert keine Visual Studio Analyzer-Ereignisse, sondern Windows-Ablaufverfolgungsereignisse.  

-   Der OLE DB-Treiber für SQL Server kann nicht mit perfmon verwendet werden. Perfmon ist ein Windows-Tool, das nur mit DSNs verwendet werden kann, die den im Lieferumfang von Windows enthaltenen MDAC SQLODBC-Treiber verwenden.  

-   Wenn eine Verbindung des OLE DB-Treibers für SQL Server mit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höheren Versionen hergestellt wird, wird Serverfehler 16947 als SQL_ERROR zurückgegeben. Dieser Fehler tritt auf, wenn ein positioniertes Update oder Löschen eine Zeile nicht aktualisieren oder löschen kann. Mit MDAC wird beim Herstellen einer Verbindung mit einer Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Serverfehler 16947 als Warnung (SQL_SUCCESS_WITH_INFO) zurückgegeben.  

-   Der OLE DB-Treiber für SQL Server implementiert die **IDBDataSourceAdmin**-Schnittstelle. Hierbei handelt es sich um eine optionale OLE DB-Schnittstelle, die zuvor nicht implementiert wurde. Es ist nur die **CreateDataSource**-Methode dieser optionalen Schnittstelle implementiert. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  

-   Der OLE DB-Treiber für SQL Server gibt Synonyme in den Schemarowsets TABLES und TABLE_INFO zurück, wobei der Wert TABLE_TYPE auf SYNONYM gesetzt ist.  

-   Rückgabewerte vom Datentyp **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, **udt** oder sonstige LOB-Typen (Large Object) können nicht an Clienttreiberversionen vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] zurückgegeben werden. Wenn Sie diese Typen als Rückgabewerte verwenden möchten, müssen Sie den OLE DB-Treiber für SQL Server verwenden.  

-   MDAC lässt die Ausführung folgender Anweisungen beim Start manueller und impliziter Transaktionen zu, während der OLE DB-Treiber für SQL Server diese Möglichkeit nicht bietet. Die Anweisungen müssen im Autocommitmodus ausgeführt werden.  

    -   Alle Volltextvorgänge (Index- und Katalog-DDL)  

    -   Alle Datenbankvorgänge (CREATE DATABASE, ALTER DATABASE, DROP DATABASE)  

    -   Neu konfigurieren  

    -   Shutdown  

    -   Beenden  

    -   Backup  

-   Wenn MDAC-Anwendungen eine Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] herstellen, werden die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Datentypen als [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-kompatible Datentypen angezeigt, wie in der folgenden Tabelle dargestellt.  

    |SQL Server 2005-Typ|SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**varchar(max)**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  

     Diese Typzuordnung beeinflusst die für Spaltenmetadaten zurückgegebenen Werte. Beispielsweise hat eine **text**-Spalte eine maximale Größe von 2.147.483.647, aber der OLE DB-Treiber für SQL Server meldet die maximale Größe von **varchar(max)** Spalten abhängig von der Plattform als 2.147.483.647 oder -1.  

-   Der OLE DB-Treiber für SQL Server lässt aus Gründen der Abwärtskompatibilität Mehrdeutigkeit in Verbindungszeichenfolgen zu. Einige Schlüsselwörter können also beispielsweise mehr als einmal angegeben werden, und konfliktverursachende Schlüsselwörter können mit einer Auflösung basierend auf der Position oder Rangfolge zugelassen werden. Zukünftige Versionen des OLE DB-Treibers für SQL Server lassen möglicherweise keine Mehrdeutigkeit in Verbindungszeichenfolgen zu. Es empfiehlt sich beim Ändern von Anwendungen, den OLE DB-Treiber für SQL Server zu verwenden, um eine Abhängigkeit von der Mehrdeutigkeit von Verbindungszeichenfolgen zu umgehen.  

-   Wenn Sie einen OLE DB-Aufruf zum Starten von Transaktionen verwenden, verhalten sich der OLE DB-Treiber für SQL Server und MDAC unterschiedlich. Mit dem OLE DB-Treiber für SQL Server werden die Transaktionen unmittelbar gestartet, mit MDAC hingegen beginnen sie erst nach dem ersten Datenbankzugriff. Dies kann sich auf das Verhalten gespeicherter Prozeduren und Batches auswirken, da @@TRANCOUNT bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nach Beenden der Ausführung eines Batches oder einer gespeicherten Prozedur unverändert gegenüber dem Startzeitpunkt des Batches oder der gespeicherten Prozedur sein muss.  

-   Mit dem OLE DB-Treiber für SQL Server bewirkt ITransactionLocal::BeginTransaction, dass eine Transaktion sofort gestartet wird. Mit MDAC wurde der Transaktionsstart verzögert, bis die Anwendung eine Anweisung ausgeführt hat, die eine Transaktion im impliziten Transaktionsmodus erforderte. Weitere Informationen finden Sie unter [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  


 Sowohl der OLE DB-Treiber für SQL Server als auch MDAC unterstützt die READ COMMITTED-Transaktionsisolation mit Zeilenversionsverwaltung, aber nur der OLE DB-Treiber für SQL Server unterstützt die Momentaufnahmen-Transaktionsisolation. (Programmiertechnisch ausgedrückt bedeutet dies, dass die Read Committed-Transaktionsisolation mit Zeilenversionsverwaltung gleichbedeutend mit einer Read Committed-Transaktion ist.)  

## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
