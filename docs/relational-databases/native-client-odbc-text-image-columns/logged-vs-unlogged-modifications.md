---
title: Protokollierte vs. nicht protokollierte Änderungen | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dc7fb913bef4083b045a0c1c010bdedbc43135c5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297664"
---
# <a name="logged-vs-unlogged-modifications"></a>Vergleich von protokollierten und nicht protokollierten Änderungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine Anwendung kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anfordern, dass der native Client ODBC-Treiber **keine Text-,** **ntext-** und **Bildänderungen** protokolliert. Diese Option sollte jedoch mit Vorsicht eingesetzt werden. Es sollte nur für Situationen verwendet werden, in denen die **Text-,** **ntext-** oder **Bilddaten** nicht kritisch sind und Datenbesitzer bereit sind, die Fähigkeit zur Wiederherstellung von Daten für eine höhere Leistung zu tauschen.  
  
 Die Protokollierung von **Text-,** **ntext-** und **Bildänderungen** wird durch Aufrufen von [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) gesteuert, wobei der *Attributparameter* auf SQL_SOPT_SS_ TEXTPTR_LOGGING festgelegt ist und *ValuePtr* auf SQL_TL_ON oder SQL_TL_OFF festgelegt ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Text und Imagespalten](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
