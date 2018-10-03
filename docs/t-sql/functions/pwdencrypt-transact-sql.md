---
title: PWDENCRYPT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aca4425147998df6679c503436b90e208e22ea16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675428"
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Kennworthash des Eingabewerts zurück, der die aktuelle Version des Kennworthashalgorithmus verwendet.  
  
 PWDENCRYPT ist eine ältere Funktion und wird in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] möglicherweise nicht mehr unterstützt werden. Verwenden Sie stattdessen [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) . HASHBYTES stellt mehr Hashalgorithmen bereit.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>Argumente  
 *password*  
 Das zu verschlüsselnde Kennwort. *password* ist **sysname**  
  
## <a name="return-types"></a>Rückgabetypen  
 **varbinary(128)**  
  
## <a name="permissions"></a>Berechtigungen  
 PWDENCRYPT steht für die Öffentlichkeit zur Verfügung.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40;Transact-SQL&#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  
