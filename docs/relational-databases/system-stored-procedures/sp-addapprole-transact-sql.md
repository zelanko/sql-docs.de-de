---
title: sp_addapprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addapprole_TSQL
- sp_addapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addapprole
ms.assetid: 24200295-9a54-4cab-9922-fb2e88632721
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4c3420396f1a8149a7c5811f1c7422a6fb960f13
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85877896"
---
# <a name="sp_addapprole-transact-sql"></a>sp_addapprole (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Fügt der aktuellen Datenbank eine Anwendungsrolle hinzu.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Create Application Role](../../t-sql/statements/create-application-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addapprole [ @rolename = ] 'role' , [ @password = ] 'password'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'`Der Name der neuen Anwendungs Rolle. *Role* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. die *Rolle* muss ein gültiger Bezeichner sein und darf nicht bereits in der aktuellen Datenbank vorhanden sein.  
  
 Namen von Anwendungsrollen können zwischen 1 und 128 Zeichen (Buchstaben, Sonderzeichen und Ziffern) enthalten. Rollennamen dürfen keinen umgekehrten Schrägstrich ( \\ ) und keinen NULL-Wert oder eine leere Zeichenfolge (' ') enthalten.  
  
`[ @password = ] 'password'`Das Kennwort, das zum Aktivieren der Anwendungs Rolle erforderlich ist. *Password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Das *Kennwort* darf nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterscheiden sich Benutzer (und Rollen) nicht vollständig von Schemas. Seit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] unterscheiden sich Schemas und Rollen vollständig. Diese neue Architektur spiegelt sich im Verhalten von CREATE APPLICATION ROLE wider. Diese Anweisung ersetzt **sp_addapprole**.  
  
 Um die Abwärtskompatibilität mit früheren Versionen von zu gewährleisten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , werden **sp_addapprole** folgende Aktionen ausführen:  
  
-   Wenn nicht bereits ein Schema mit dem gleichen Namen wie die Anwendungsrolle vorhanden ist, wird ein solches Schema erstellt. Das neue Schema ist im Besitz der Anwendungsrolle und wird als Standardschema der Anwendungsrolle verwendet.  
  
-   Wenn bereits ein Schema mit dem gleichen Namen wie die Anwendungsrolle vorhanden ist, erzeugt die Prozedur einen Fehler.  
  
-   Die Kenn Wort Komplexität wird nicht von **sp_addapprole**geprüft. Von CREATE APPLICATION ROLE hingegen wird die Kennwortkomplexität überprüft.  
  
 Das Parameter *Kennwort* wird als unidirektionaler Hash gespeichert.  
  
 Die gespeicherte Prozedur **sp_addapprole** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
> [!IMPORTANT]  
>  Die Microsoft ODBC- **Verschlüsselungs** Option wird von **SqlClient**nicht unterstützt. Sofern möglich, sollten Benutzer zur Eingabe der Anmeldeinformationen für Anwendungsrollen zur Laufzeit aufgefordert werden. Die Anmeldeinformationen sollten nicht in einer Datei gespeichert werden. Wenn Anmeldeinformationen persistent gespeichert werden müssen, sollten Sie sie mithilfe der CryptoAPI-Funktionen verschlüsseln.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank. Ist nicht bereits ein Schema mit dem gleichen Namen und Besitzer wie die neue Rolle vorhanden, ist auch die CREATE SCHEMA-Berechtigung für die Datenbank erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktuellen Datenbank die neue Anwendungs Rolle `SalesApp` mit dem Kennwort hinzugefügt `x97898jLJfcooFUYLKm387gf3` .  
  
```  
EXEC sp_addapprole 'SalesApp', 'x97898jLJfcooFUYLKm387gf3' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)  
  
  
