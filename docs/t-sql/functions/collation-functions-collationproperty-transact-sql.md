---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 66a53dcece274df879242ac8a7d3315882bad84f
ms.sourcegitcommit: d6ef87a01836738b5f7941a68ca80f98c61a49d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57572793"
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Sortierungsfunktionen: COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Diese Funktion gibt die angeforderte Eigenschaft einer angegebenen Sortierung zurück.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Argumente  
*collation_name*  
Der Name der Sortierung. Das Argument *collation_name* weist den Datentyp **nvarchar(128)** auf und verfügt über keinen Standardwert.
  
*property*  
Die Eigenschaft der Sortierung. Das Argument *property* weist den Datentyp **varchar(128)** auf und kann einen der folgenden Werte besitzen:
  
|Eigenschaftenname|Beschreibung|  
|---|---|
|**CodePage**|Nicht-Unicode-Codepage der Sortierung. Dies ist der Zeichensatz, der für **varchar**-Daten verwendet wird. Informationen zum Übersetzen dieser Werte und zu ihren Zeichenzuordnungen finden Sie unter [Appendix G DBCS/Unicode Mapping Tables (Anhang G: Tabellen zur DBCS-/Unicode-Zuordnung)](https://msdn.microsoft.com/library/cc194886.aspx) und [Appendix H Code Pages (Anhang H: Codepages)](https://msdn.microsoft.com/library/cc195051.aspx).<br /><br />Basisdatentyp: **int**|  
|**LCID**|Windows-Gebietsschemabezeichner (Locale Identifier, LCID) der Sortierung. Dies ist die Kultur, die für die Sortierung und die Vergleichsregeln verwendet wird. Informationen zum Übersetzen dieser Werte erhalten Sie unter [LCID Structure (LCID-Struktur)](https://msdn.microsoft.com/library/cc233968.aspx). Sie müssen jedoch zunächst eine Konvertierung in **varbinary** vornehmen.<br /><br />Basisdatentyp: **int**|  
|**ComparisonStyle**|Die Windows-Vergleichsart der Sortierung. Gibt 0 für binäre Sortierungen zurück. Sowohl (\_BIN) als auch (\_BIN2) werden ebenfalls zurückgegeben, wenn nach allen Eigenschaften unterschieden wird – (\_CS\_AS\_KS\_WS) und (\_CS\_AS\_KS\_WS\_SC) und (\_CS\_AS\_KS\_WS\_VSS). Bitmaskenwerte:<br /><br /> Groß-/Kleinschreibung ignorieren: 1<br /><br /> Akzente ignorieren: 2<br /><br /> Kana ignorieren: 65536<br /><br /> Breite ignorieren: 131072<br /><br /> Hinweis: Die Option \_VSS (Unterscheidung nach Variierungsauswahlzeichen) wird in diesem Wert nicht dargestellt, obwohl sie Auswirkungen auf das Vergleichsverhalten hat.<br /><br />Basisdatentyp: **int**|  
|**Version**|Die Version der Sortierung. Gibt einen Wert zwischen 0 und 3 zurück.<br /><br /> Sortierungen, in deren Namen die Zahl 140 enthalten ist, geben 3 zurück.<br /><br /> Sortierungen, in deren Namen die Zahl 100 enthalten ist, geben 2 zurück.<br /><br /> Sortierungen, in deren Namen die Zahl 90 enthalten ist, geben 1 zurück.<br /><br /> Alle anderen Sortierungen geben 0 zurück.<br /><br />Basisdatentyp: **tinyint**|  
  
## <a name="return-types"></a>Rückgabetypen
**sql_variant**
  
## <a name="examples"></a>Beispiele  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>Siehe auch
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

