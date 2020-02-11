---
title: Native Client, Aktualisieren von App-SQL von MDAC
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQLNCLI, vs. MDAC
- SQL Server Native Client, vs. MDAC
- data access [SQL Server Native Client], vs. MDAC
- SQL Server Native Client, updating applications
ms.assetid: 2860efdd-c59a-4deb-8a0e-5124a8f4e6dd
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f8f6b7efd8d97f63e93061cbef1a54e1df3146d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243787"
---
# <a name="updating-an-application-to-sql-server-native-client-from-mdac"></a>Aktualisieren einer Anwendung von MDAC auf SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Es gibt eine Reihe von Unterschieden zwischen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und Microsoft Data Access Components (MDAC; ab Windows Vista werden die Datenzugriffskomponenten als Windows Data Access Components oder Windows DAC bezeichnet). Durch beide Technologien wird systemeigener Datenzugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken bereitgestellt, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQL Native Client wurde jedoch speziell für die Verwendung der neuen Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] entwickelt und bietet gleichzeitig Abwärtskompatibilität mit früheren Versionen.  
  
 Anhand der Informationen in diesem Thema können Sie die MDAC-Anwendung (oder Windows DAC) auf die Version [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client aktualisieren, die im Lieferumfang von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] enthalten ist. Informationen dazu, wie Sie diese Anwendung mit der Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, die in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]ausgeliefert wird, aktuell machen können, finden Sie unter [Aktualisieren einer Anwendung aus SQL Server 2005 Native Client](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md).  
  
 Obwohl MDAC Komponenten zur Verwendung von OLE DB, ODBC und ActiveX Data Objects (ADO) enthält, implementiert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client nur OLE DB und ODBC (ADO hat allerdings Zugriff auf die Funktionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client).  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und MDAC unterscheiden sich in anderen Bereichen wie folgt:  
  
-   Benutzern, die mit ADO auf einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Anbieter zugreifen, stehen möglicherweise weniger Filterfunktionen zur Verfügung als bei Zugriff auf einen SQL OLE DB-Anbieter.  
  
-   Wenn eine ADO-Anwendung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet und versucht, eine berechnete Spalte zu aktualisieren, wird ein Fehler gemeldet. Mit MDAC wurde das Update akzeptiert, jedoch ignoriert.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ist eine einzelne, eigenständige Dynamic Link Library-Datei (DLL). Die öffentlich verfügbaren Schnittstellen wurden auf ein Minimum reduziert, um sowohl die Verteilung zu erleichtern als auch die Sicherheitsrisiken einzuschränken.  
  
-   Es werden nur OLE DB und ODBC-Schnittstellen unterstützt.  
  
-   Die Namen des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieters und des ODBC-Treibers unterscheiden sich von den mit MDAC verwendeten Namen.  
  
-   Mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sind von MDAC-Komponenten bereitgestellte Benutzerzugriffsfunktionen verfügbar. Dazu gehören u. a.: Verbindungspooling, ADO-Unterstützung und Clientcursorunterstützung. Wenn eine dieser Funktionen verwendet wird, stellt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client nur Datenbankkonnektivität zur Verfügung. MDAC stellt Funktionen wie Ablaufverfolgung, Verwaltungssteuerelemente und Leistungsindikatoren bereit.  
  
-   Anwendungen können die OLE DB-Basisdienste mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwenden. Bei Verwendung der OLE DB-Cursor-Engine sollten sie jedoch die Datentyp-Kompatibilitätsoption verwenden, um potenzielle Probleme zu vermeiden, die auftreten können, da die Cursor-Engine die neuen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Datentypen nicht erkennt.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt den Zugriff auf Datenbanken früherer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Versionen.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält keine XML-Integration. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client unterstützt SELECT... FOR XML-Abfragen, unterstützt jedoch keine anderen XML-Funktionen. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt jedoch den in **** [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]eingeführten XML-Datentyp.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt das Konfigurieren clientseitiger Netzwerkbibliotheken nur mithilfe von Verbindungszeichenfolgenattributen. Wenn Sie eine umfassendere Netzwerkbibliothekskonfiguration benötigen, müssen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager verwenden.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ist nicht kompatibel mit odbcbcp.dll. Anwendungen, die sowohl ODBC-als auch **bcp** -APIs verwenden, müssen neu erstellt werden, um mit sqlncli11 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . lib verknüpft zu werden, um Native Client zu verwenden.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wird vom Microsoft OLE DB-Anbieter für ODBC (MSDASQL) nicht unterstützt. Wenn Sie den MDAC SQLODBC-Treiber mit MSDASQL oder mit ADO verwenden, sollten Sie in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB verwenden.  
  
-   MDAC-Verbindungs Zeichenfolgen lassen einen booleschen Wert (**true**) für das **Trusted_Connection** -Schlüsselwort zu. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eine Native Client-Verbindungs Zeichenfolge muss **Yes** oder **No**verwendet werden.  
  
-   An Warnungen und Fehlern wurden geringfügige Änderungen vorgenommen. Vom Server zurückgegebene Warnungen und Fehler behalten bei Übergabe an den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den gleichen Schweregrad bei. Sie sollten sicherstellen, dass die Anwendung gründlich getestet wurde, wenn Sie auf das Abfangen bestimmter Warnungen und Fehler angewiesen sind.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client enthält eine strengere Fehlerprüfung als MDAC. Dies bedeutet, dass einige Anwendungen, die den ODBC- und OLE DB-Spezifikationen nicht hundertprozentig entsprechen, sich anders verhalten. Der SQLOLEDB-Anbieter hat z. b. die Regel nicht erzwungen, dass Parameternamen für\@Ergebnis Parameter mit ' ' beginnen müssen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , aber der Native Client OLE DB-Anbieter.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verhält sich in Bezug auf fehlgeschlagene Verbindungen anders als MDAC. MDAC gibt beispielsweise zwischengespeicherte Eigenschaftswerte für eine fehlgeschlagene Verbindung zurück, während [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client einen Fehler an die aufrufende Anwendung meldet.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client generiert keine Visual Studio Analyzer-Ereignisse, sondern stattdessen Windows-Ablaufverfolgungsereignisse.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client kann nicht mit perfmon verwendet werden. Perfmon ist ein Windows-Tool, das nur mit DSNs verwendet werden kann, die den im Lieferumfang von Windows enthaltenen MDAC SQLODBC-Treiber verwenden.  
  
-   Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client mit [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höheren Versionen verbunden wird, wird Serverfehler 16947 als SQL_ERROR zurückgegeben. Dieser Fehler tritt auf, wenn ein positioniertes Update oder Löschen eine Zeile nicht aktualisieren oder löschen kann. Mit MDAC wird beim Herstellen einer Verbindung mit einer Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Serverfehler 16947 als Warnung (SQL_SUCCESS_WITH_INFO) zurückgegeben.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client implementiert die **IDBDataSourceAdmin** -Schnittstelle. dabei handelt es sich um eine optionale OLE DB-Schnittstelle, die zuvor nicht implementiert wurde, aber nur die Methode " **kreatedatasource** " dieser optionalen Schnittstelle implementiert wird. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt Synonyme in den Schemarowsets TABLES und TABLE_INFO zurück, wobei der Wert TABLE_TYPE auf SYNONYM gesetzt ist.  
  
-   Rückgabewerte des Datentyps **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **UDT**oder andere Typen von großen Objekten können nicht an Client Versionen vor zurück [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]gegeben werden. Wenn Sie diese Typen als Rückgabewerte verwenden möchten, müssen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwenden.  
  
-   MDAC lässt die Ausführung folgender Anweisungen beim Start manueller und impliziter Transaktionen zu, während [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client diese Möglichkeit nicht bietet. Die Anweisungen müssen im Autocommitmodus ausgeführt werden.  
  
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
    |**varbinary(max)**|**Klang**|  
    |**UDT**|**varbinary**|  
    |**basi**|**ntext**|  
  
     Diese Typzuordnung beeinflusst die für Spaltenmetadaten zurückgegebenen Werte. Beispielsweise hat eine **Text** Spalte eine maximale Größe von 2.147.483.647 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , aber Native Client ODBC meldet die maximale Größe von **varchar (max)** -Spalten als SQL_SS_LENGTH_UNLIMITED, und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB meldet die maximale Größe von **varchar (max)** -Spalten als 2.147.483.647 oder-1, abhängig von der Plattform.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lässt aus Gründen der Abwärtskompatibilität Mehrdeutigkeit in Verbindungszeichenfolgen zu (einige Schlüsselwörter können beispielsweise mehr als einmal angegeben werden, und konfliktverursachende Schlüsselwörter können mit einer Auflösung basierend auf der Position oder Rangfolge zugelassen werden). Zukünftige Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lassen möglicherweise keine Mehrdeutigkeit in Verbindungszeichenfolgen zu. Es empfiehlt sich beim Ändern von Anwendungen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu verwenden, um eine Abhängigkeit von der Mehrdeutigkeit von Verbindungszeichenfolgen zu umgehen.  
  
-   Wenn Sie einen ODBC- oder OLE DB-Aufruf zum Starten von Transaktionen verwenden, verhalten sich [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und MDAC unterschiedlich. Mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client werden die Transaktionen unmittelbar gestartet, mit MDAC hingegen beginnen sie erst nach dem ersten Datenzugriff. Dies kann sich auf das Verhalten gespeicherter Prozeduren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und \@ \@Batches auswirken, da nach der Ausführung eines Batches oder einer gespeicherten Prozedur die Ausführung von nach der Ausführung des Batches oder der gespeicherten Prozedur erforderlich ist.  
  
-   Mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client bewirkt itransaktionlocal:: BeginTransaction, dass eine Transaktion sofort gestartet wird. Mit MDAC wurde der Transaktionsstart verzögert, bis die Anwendung eine Anweisung ausgeführt hat, die eine Transaktion im impliziten Transaktionsmodus erforderte. Weitere Informationen finden Sie unter [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
-   Möglicherweise treten Fehler auf, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Wenn Sie den Native Client-Treiber mit System. Data. ODBC verwenden, um auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Server Computer zuzugreifen, der neue,-spezifische Datentypen oder Features verfügbar macht. System. Data. ODBC stellt eine generische ODBC-Implementierung bereit und macht anschließend keine herstellerspezifischen Funktionen oder Erweiterungen verfügbar. (Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Treiber wird aktualisiert, um die neuesten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Features nativ zu unterstützen.) Um dieses Problem zu umgehen, können Sie entweder zu MDAC zurückkehren oder zu System. Data. SqlClient migrieren.  
  
 Sowohl [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als auch MDAC unterstützen die Read Committed-Isolation mit Zeilenversionsverwaltung, aber nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt die Momentaufnahmen-Transaktionsisolation. (Programmiertechnisch ausgedrückt bedeutet dies, dass die Read Committed-Transaktionsisolation mit Zeilenversionsverwaltung gleichbedeutend mit einer Read Committed-Transaktion ist.)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
