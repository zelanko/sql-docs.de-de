---
title: Protokollierte im Vergleich zu Nicht protokollierte Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34064aaa2e96a7d610f8709c1f5750bddd62b766
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420290"
---
# <a name="logged-vs-unlogged-modifications"></a>Protokollierte im Vergleich zu Nicht protokollierte Änderungen
  Kann eine Anwendung anfordern, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber nicht protokolliert **Text**, **Ntext**, und **Image** Änderungen. Diese Option sollte jedoch mit Vorsicht eingesetzt werden. Es sollte nur für diese Fälle verwendet werden, in denen die **Text**, **Ntext**, oder **Image** Daten sind nicht kritische und Besitzer der Daten bereit sind, die Möglichkeit zum Wiederherstellen von Daten für die Kompromisse höhere Leistung.  
  
 Die Protokollierung von **Text**, **Ntext**, und **Image** Änderungen wird gesteuert, durch den Aufruf [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) mit der  *Attribut* Parameter legen auf SQL_SOPT_SS_ TEXTPTR_LOGGING und *ValuePtr* legen Sie entweder auf SQL_TL_ON oder auf sql_tl_off festgelegt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Text und Imagespalten](managing-text-and-image-columns.md)  
  
  
