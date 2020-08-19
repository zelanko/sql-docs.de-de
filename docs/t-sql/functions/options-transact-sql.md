---
description: '&#x40;&#x40;OPTIONS (Transact-SQL)'
title: '@@OPTIONS (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@OPTIONS'
- '@@OPTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, current SET options
- '@@OPTIONS function'
- current SET options
ms.assetid: 3d5c7f6e-157b-4231-bbb4-4645a11078b3
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 12e2d3418a021a3ffee5db530d35f0fc8522dec1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417226"
---
# <a name="x40x40options-transact-sql"></a>&#x40;&#x40;OPTIONS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt Informationen zu den aktuellen SET-Optionen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
@@OPTIONS  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 **integer**  
  
## <a name="remarks"></a>Bemerkungen  
 Die Optionen werden zurückgegeben, wenn Sie den **SET**-Befehl oder die **sp_configure-Benutzeroptionen** verwenden. Mithilfe des **SET**-Befehls konfigurierte Sitzungswerte überschreiben die **sp_configure**-Optionen. Viele Tools (beispielsweise [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]) konfigurieren SET-Optionen automatisch. Jeder Benutzer verfügt über eine @@OPTIONS-Funktion, die die Konfiguration darstellt.  
  
 Sie können die Sprache und die Abfrageverarbeitungsoptionen für eine bestimmte Benutzersitzung mithilfe der SET-Anweisung ändern. **\@\@OPTIONS** kann nur die Optionen erkennen, die auf ON oder OFF festgelegt sind.  
  
 Die **\@\@OPTIONS**-Funktion gibt eine Bitmap der Optionen zurück, die in einen Integer zur Basis 10 (dezimal) konvertiert wurde. Die Biteinstellungen werden an den in einer Tabelle im Artikel [Konfigurieren der Benutzeroptionen für die Serverkonfigurationsoption](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) beschriebenen Orten gespeichert.  
  
 Konvertieren Sie den von **\@\@OPTIONS** zurückgegebenen Integer in das Binärformat, und suchen Sie in der unter [Konfigurieren der Benutzeroptionen für die Serverkonfigurationsoption](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) aufgeführten Tabelle nach den Werten, um den **\@\@OPTIONS**-Wert zu decodieren. Wenn beispielsweise `SELECT @@OPTIONS;` den Wert `5496` zurückgibt, verwenden Sie den Windows-Rechner (**calc.exe**), um die Dezimalzahl `5496` ins Binärformat zu konvertieren. Das Ergebnis ist `1010101111000`. Die am weitesten rechts stehenden Zeichen (Binärwerte 1, 2 und 4) haben den Wert 0 (null), was darauf hindeutet, dass die ersten drei Elemente in der Tabelle deaktiviert sind. In der Tabelle sehen Sie, dass die Elemente **DISABLE_DEF_CNST_CHK**, **IMPLICIT_TRANSACTIONS** und **CURSOR_CLOSE_ON_COMMIT** lauten. Das nächste Element (**ANSI_WARNINGS** an der Position `1000`) ist aktiviert. Fahren Sie auf der linken Seite mit der Bitmap und der Liste der Optionen fort. Wenn die ganz links stehenden Optionen einen Wert von 0 (null) aufweisen, wurden sie durch die Typkonvertierung abgeschnitten. Bei der Bitmap `1010101111000` handelt es sich tatsächlich um `001010101111000`, um alle 15 Optionen darzustellen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-demonstration-of-how-changes-affect-behavior"></a>A. So wirken sich Änderungen auf das Verhalten aus  
 Das folgende Beispiel veranschaulicht die Unterschiede im Verkettungsverhalten bei Verwendung zweier verschiedener Einstellungen für die Option **CONCAT_NULL_YIELDS_NULL**.  
  
```  
SELECT @@OPTIONS AS OriginalOptionsValue;  
SET CONCAT_NULL_YIELDS_NULL OFF;  
SELECT 'abc' + NULL AS ResultWhen_OFF, @@OPTIONS AS OptionsValueWhen_OFF;  
  
SET CONCAT_NULL_YIELDS_NULL ON;  
SELECT 'abc' + NULL AS ResultWhen_ON, @@OPTIONS AS OptionsValueWhen_ON;  
```  
  
### <a name="b-testing-a-client-nocount-setting"></a>B. Testen einer NOCOUNT-Clienteinstellung  
 Das folgende Beispiel legt `NOCOUNT``ON` fest und testet dann den Wert von `@@OPTIONS`. Die Option `NOCOUNT``ON` verhindert, dass die Nachricht über die Anzahl von betroffenen Zeilen an den anfordernden Client für jede Anweisung in einer Sitzung zurückgegeben wird. Für den Wert von `@@OPTIONS` wird `512` (0x0200) festgelegt. Dies stellt die Option NOCOUNT dar. Dieses Beispiel testet, ob die Option NOCOUNT auf dem Client aktiviert wurde. Dadurch können beispielsweise Leistungsunterschiede auf einem Client nachverfolgt werden.  
  
```  
SET NOCOUNT ON  
IF @@OPTIONS & 512 > 0   
RAISERROR ('Current user has SET NOCOUNT turned on.', 1, 1)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurationsfunktionen (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Konfigurieren der Serverkonfigurationsoption Benutzeroptionen](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)  
  
  
