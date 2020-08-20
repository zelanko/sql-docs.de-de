---
description: ALTER CREDENTIAL (Transact-SQL)
title: ALTER CREDENTIAL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER CREDENTIAL
- ALTER_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], credentials
- credentials [SQL Server], ALTER CREDENTIAL statement
- modifying credentials
- authentication [SQL Server], credentials
- ALTER CREDENTIAL statement
ms.assetid: b08899a6-c09e-4af4-91aa-a978ada79264
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 8c251486ae982abda531bd443db95c57a1b99900
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479236"
---
# <a name="alter-credential-transact-sql"></a>ALTER CREDENTIAL (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert die Eigenschaften von Anmeldeinformationen.  

> [!IMPORTANT]
> Informationen mit „Sollte“ stehen für bewährte Methoden, Informationen mit „Muss“ sind zum Abschließen eines Tasks erforderlich. ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
ALTER CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *credential_name*  
 Gibt den Namen der Anmeldeinformationen an, die geändert werden.  
  
 IDENTITY **='***identity_name***'**  
 Gibt den Namen des Kontos an, das beim Herstellen einer Verbindung außerhalb des Servers verwendet wird.  
  
 SECRET **='***secret***'**  
 Gibt den geheimen Bereich an, der für die ausgehende Authentifizierung erforderlich ist. *secret* ist optional.
  
> [!IMPORTANT]
> Azure SQL-Datenbank unterstützt nur Azure Key Vault- und Shared Access Signature-Identitäten. Windows-Benutzeridentitäten werden nicht unterstützt.
  
## <a name="remarks"></a>Hinweise  
 Wenn Anmeldeinformationen geändert werden, werden die Werte von *identity_name* und *secret* zurückgesetzt. Falls das optionale SECRET-Argument nicht angegeben wird, wird der Wert des gespeicherten Kennworts auf NULL festgelegt.  
  
 Das Kennwort wird mithilfe des Diensthauptschlüssels verschlüsselt. Falls der Diensthauptschlüssel erneut generiert wird, wird das Kennwort erneut mithilfe des neuen Diensthauptschlüssels verschlüsselt.  
  
 Informationen zu Anmeldeinformationen werden in der **sys.credentials**-Katalogsicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY CREDENTIAL-Berechtigung. Falls es sich bei dem Anmeldeinformationen um Systemanmeldeinformationen handelt, ist die CONTROL SERVER-Berechtigung erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-changing-the-password-of-a-credential"></a>A. Ändern des Kennworts für Anmeldeinformationen  
 Im folgenden Beispiel wird das Kennwort, das in den Anmeldeinformationen namens `Saddles` gespeichert ist, geändert. Diese Anmeldeinformationen enthalten den Windows-Anmeldenamen `RettigB` und das zugehörige Kennwort. Das neue Kennwort wird den Anmeldeinformationen mithilfe der SECRET-Klausel hinzugefügt.  
  
```  
ALTER CREDENTIAL Saddles WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. Entfernen des Kennworts aus Anmeldeinformationen  
 Im folgenden Beispiel wird das Kennwort aus Anmeldeinformationen namens `Frames` entfernt. Diese Anmeldeinformationen enthalten den Windows-Anmeldenamen `Aboulrus8` und ein Kennwort. Nach der Ausführung der Anweisung weisen die Anmeldeinformationen ein NULL-Kennwort auf, weil die Option SECRET nicht angegeben ist.  
  
```  
ALTER CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anmeldeinformationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [DROP CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
