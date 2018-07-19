---
title: Anmeldeinformationen (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 579b9d6f9847652ab2088eeb5111372fc4377c02
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198780"
---
# <a name="credentials-database-engine"></a>Anmeldeinformationen (Datenbank-Engine)
  Anmeldeinformationen sind in einem Datensatz gespeichert, in dem die Authentifizierungsinformationen (Anmeldeinformationen) enthalten sind, die zum Herstellen einer Verbindung mit einer Ressource außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]erforderlich sind. Diese Informationen werden intern von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet. Die meisten Anmeldeinformationen enthalten einen Windows-Benutzernamen und ein Kennwort.  
  
 Die in Anmeldeinformationen gespeicherten Informationen ermöglichen einem Benutzer, der eine Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung hergestellt hat, auf Ressourcen außerhalb der Serverinstanz zuzugreifen. Wenn es sich bei der externen Ressource um Windows handelt, wird der Benutzer als der in den Anmeldeinformationen angegebene Windows-Benutzer authentifiziert. Eine einzelne Anmeldung kann mehreren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldungen zugeordnet werden. Eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung kann allerdings nur einer Anmeldung zugeordnet werden.  
  
 Systemanmeldeinformationen werden automatisch erstellt und mit bestimmten Endpunkten verbunden. Namen für Systemanmeldeinformationen beginnen mit zwei Nummernzeichen (##).  
  
 Weitere Informationen zu Anmeldeinformationen finden Sie unter den [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) -Katalogsicht angezeigt.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Erstellen von Anmeldeinformationen](../authentication-access/create-a-credential.md) [Erstellung von Anmeldeinformationen &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
 [Sichern von SQL Server](../securing-sql-server.md)  
  
  
