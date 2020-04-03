---
title: Sichere Kennwörter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 297dc4127fbfd040ba0d9cc970f3a044395b5e21
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "79448221"
---
# <a name="strong-passwords"></a>Sichere Kennwörter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Kennwörter sind möglicherweise das schwächste Glied bei der Bereitstellung von Serversicherheit. Gehen Sie bei der Auswahl eines Kennworts mit Vorsicht vor. Ein sicheres Kennwort weist die folgenden Merkmale auf:  
  
-   Es ist mindestens acht Zeichen lang.  
  
-   Es besteht aus einer Kombination aus Buchstaben, Ziffern und Sonderzeichen.  
  
-   Es wird in keinem Wörterbuch aufgeführt.  
  
-   Es handelt sich nicht um einen Befehlsnamen.  
  
-   Es handelt sich nicht um den Namen einer Person.  
  
-   Es handelt sich nicht um den Namen eines Benutzers.  
  
-   Es handelt sich nicht um einen Computernamen.  
  
-   Es wird regelmäßig geändert.  
  
-   Es unterscheidet sich von zuvor verwendeten Kennwörtern.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Kennwörter können bis zu 128 Zeichen (einschließlich Buchstaben, Sonderzeichen und Ziffern) enthalten. Bestimmte Symbole müssen jedoch von doppelten Anführungszeichen (") oder eckigen Klammern ([ ]) eingeschlossen werden, da Benutzernamen, Benutzer, Rollen und Kennwörter häufig in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwendet werden. Verwenden Sie diese Trennzeichen in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, wenn die Anmeldenamen, Benutzer, Rollen und Kennwörter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] folgende Merkmale aufweisen:  
  
-   Das Element enthält oder beginnt mit einem Leerzeichen.  
  
-   Das Element beginnt mit dem Zeichen $ oder \@.  
  
 Bei Verwendung in einer OLE DB- oder ODBC-Verbindungszeichenfolge dürfen die folgenden Zeichen nicht in einem Anmeldenamen oder Kennwort enthalten sein: [] () , ; ? * ! \@ =. Mithilfe dieser Zeichen wird entweder eine Verbindung initialisiert oder Verbindungswerte werden getrennt.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)  
  
  
