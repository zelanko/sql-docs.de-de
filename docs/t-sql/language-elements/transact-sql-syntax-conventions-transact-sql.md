---
title: Transact-SQL-Syntaxkonventionen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- sql13.TSQLExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- conventions [SQL Server]
- Applies to section in Transact-SQL topics
- code example conventions [SQL Server]
- objects [SQL Server], names
- code [SQL Server], conventions
- multipart names [SQL Server]
- Transact-SQL syntax conventions
- syntax conventions [SQL Server]
- code [SQL Server]
- Transact-SQL
- naming conventions [SQL Server]
- syntax [SQL Server], Transact-SQL
ms.assetid: 35fbcf7f-8b55-46cd-a957-9b8c7b311241
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0580ed82ca6ab5d94b1411ba70ce1b0d2f3ff770
ms.sourcegitcommit: c61c7b598aa61faa34cd802697adf3a224aa7dc4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56154715"
---
# <a name="transact-sql-syntax-conventions-transact-sql"></a>Transact-SQL-Syntaxkonventionen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

In der folgenden Tabelle werden die Konventionen aufgeführt und beschrieben, die in den Syntaxdiagrammen in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Referenz verwendet werden.  
  
|Konvention|Syntaxelemente|  
|----------------|--------------|  
|GROSSBUCHSTABEN|[!INCLUDE[tsql](../../includes/tsql-md.md)]-Schlüsselwörter.|  
|_Kursiv_|Vom Benutzer anzugebende Parameter der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Syntax.|  
|**Fett**|Geben Sie Datenbanknamen, Tabellennamen, Spaltennamen, Indexnamen, gespeicherte Prozeduren, Hilfsprogramme, Datentypnamen und Text genau wie angegeben ein.|  
|Unterstrichen|Gibt den Standardwert an, der verwendet wird, wenn die Klausel mit dem unterstrichenen Wert in der Anweisung ausgelassen wird.|  
|&#124; (Senkrechter Strich)|Trennt in eckigen oder geschweiften Klammern eingeschlossene Syntaxelemente. Sie können nur eines der Elemente verwenden.|  
|`[ ]` (eckige Klammern)|Optionale Syntaxelemente. Geben Sie die Klammern nicht mit ein.|  
|{ } (geschweifte Klammern)|Erforderliche Syntaxelemente. Geben Sie die geschweiften Klammern nicht mit ein.|  
|[**,**..._n_]|Zeigt an, dass das vorherige Element _n_ -mal wiederholt werden kann. Die einzelnen Vorkommen werden durch Kommas voneinander getrennt.|  
|[..._n_]|Zeigt an, dass das vorherige Element _n_ -mal wiederholt werden kann. Die einzelnen Vorkommen werden durch Leerzeichen voneinander getrennt.|  
|;|Abschlusszeichen für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. Dieses Abschlusszeichen ist für die meisten Anweisungen in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht erforderlich, jedoch in einer zukünftigen Version.|  
|\<label> ::=|Der Name eines Syntaxblockes. Verwenden Sie diese Konvention zur Gruppierung und Bezeichnung von Abschnitten einer langen Syntax oder einer Syntaxeinheit, die Sie an mehreren Stellen innerhalb einer Anweisung verwenden können. Jede Stelle, an der der Syntaxblock verwendet werden könnte, wird durch die in spitze Klammern eingeschlossene Bezeichnung angezeigt: \<label>.<br /><br /> Ein Set ist eine Collection von Ausdrücken, z.B. \<Gruppierungssatz>. Eine Liste ist eine Collection von Sets, z.B. \<Liste zusammengesetzter Elemente>.|  
  
## <a name="multipart-names"></a>Mehrteilige Namen  
Wenn keine anderen Angaben vorliegen, können alle [!INCLUDE[tsql](../../includes/tsql-md.md)]-Referenzen auf den Namen eines Datenbankobjekts aus vier Teilen bestehende Namen im folgenden Format sein:  
  
_server\_name_.[_database\_name_].[_schema\_name_]._object\_name_  
  
| _database\_name_.[_schema\_name_]._object\_name_  
 
| _schema\_name_._object\_name_  
  
| _object\_name_  
  
_server\_name_  
Gibt den Namen eines Verbindungs- oder Remoteservers an.  
  
_database\_name_  
Gibt den Namen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank an, wenn sich das Objekt in einer lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet. Wenn sich das Objekt auf einem verknüpften Server befindet, wird mit *database_name* ein OLE DB-Katalog angegeben.  
  
_schema\_name_  
Gibt den Namen des Schemas an, das das Objekt enthält, wenn sich das Objekt in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank befindet. Wenn sich das Objekt auf einem Verbindungsserver befindet, wird mit *schema_name* ein OLE DB-Schemaname angegeben.  
  
_object\_name_  
Gibt den Namen des Objekts an.  
  
Wenn Sie auf ein bestimmtes Objekt verweisen, müssen Sie nicht immer den Server, die Datenbank und das Schema angeben, damit das Objekt vom [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] identifiziert werden kann. Wenn das Objekt jedoch nicht gefunden werden kann, wird ein Fehler zurückgegeben.  
  
> [!NOTE]  
> Um Fehler bei der Namensauflösung zu vermeiden, wird empfohlen, den Schemanamen bei jeder Angabe eines Objekts anzugeben, das Schemas als Bereiche besitzt.  
  
Um Zwischenknoten wegzulassen, verwenden Sie Punkte, um diese Positionen anzuzeigen. In der folgenden Tabelle sind die gültigen Formate für Objektnamen aufgeführt.  
  
|Objektverweisformat|und Beschreibung|  
|-----------------------------|-----------------|  
|_server_._database_._schema_._object_|Vierteiliger Name.|  
|_server_._database_.._object_|Der Schemaname wird weggelassen.|  
|_server_.._schema_._object_|Der Datenbankname wird weggelassen.|  
|_server_..._object_|Der Datenbank- und der Schemaname werden weggelassen.|  
|_database_._schema_._object_|Der Servername wird weggelassen.|  
|_database_.._object_|Der Server- und der Schemaname werden weggelassen.|  
|_schema_._object_|Der Server- und der Datenbankname werden weggelassen.|  
|_object_|Der Server-, der Datenbank- und der Schemaname werden weggelassen.|  
  
## <a name="code-example-conventions"></a>Konventionen für Codebeispiele  
Wenn nicht anders angegeben, wurden die Beispiele in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Referenz anhand von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] und den Standardeinstellungen für die folgenden Optionen getestet:  
  
-   ANSI_NULLS  
-   ANSI_NULL_DFLT_ON  
-   ANSI_PADDING  
-   ANSI_WARNINGS  
-   CONCAT_NULL_YIELDS_NULL  
-   QUOTED_IDENTIFIER  
  
Die meisten Codebeispiele in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Referenz wurden auf Servern getestet, auf denen eine Sortierreihenfolge gilt, bei der die Groß-/Kleinschreibung beachtet wird. Auf den Testservern wurde in der Regel die ANSI/ISO-Codepage 1252 verwendet.  
  
Vielen Codebeispielen gehen Unicode-Zeichenfolgenkonstanten mit dem Buchstaben **N** voran. Ohne das **N**-Präfix wird die Zeichenfolge in die Standardcodepage der Datenbank konvertiert. Diese Standardcodepage erkennt möglicherweise bestimmte Zeichen nicht.  
  
## <a name="applies-to-references"></a>„Applies to“-Verweise  
Der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Verweis enthält Artikel im Zusammenhang mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] und [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)].   

Am oberen Rand jedes Artikels befindet sich ein Abschnitt, der angibt, welche Produkte den Betreff des Artikels unterstützen. Wenn ein Produkt fehlt, ist das im Artikel beschriebene Feature in diesem Produkt nicht verfügbar. Beispielsweise wurden Verfügbarkeitsgruppen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] eingeführt. Der **CREATE AVAILABILITY GROUP**-Artikel gilt für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), weil er für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] nicht gilt.  
  
Der allgemeine Betreff des Artikels könnte auf ein Produkt zutreffen, aber in einigen Fällen werden nicht alle Argumente unterstützt. Beispielsweise wurden Benutzer für eigenständige Datenbank in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eingeführt. Verwenden Sie die Anweisung **CREATE USER** in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Produkt, die Syntax **WITH PASSWORD** kann jedoch nicht mit älteren Versionen verwendet werden. Zusätzliche **Applies to**-Abschnitte werden in den entsprechenden Argumentbeschreibungen in den Text des Artikels eingefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](../../t-sql/transact-sql-reference-database-engine.md)    
[Reservierte Schlüsselwörter &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)      
[Transact-SQL-Entwurfsprobleme](https://msdn.microsoft.com/library/dd193411.aspx)    
[Transact-SQL-Benennungsprobleme](https://msdn.microsoft.com/library/dd193246.aspx)        
[Transact-SQL-Leistungsprobleme](https://msdn.microsoft.com/library/dd172117.aspx)    


