---
title: Tabellenwert Parameter-Metadaten für vorbereitete Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 17b96f9a18e2b076bda76550b8796301f815c9f5
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73790731"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Tabellenwertparameter-Metadaten für vorbereitete Anweisungen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Eine Anwendung kann über SQLNumParams und SQLDescribeParam Metadaten für einen vorbereiteten Prozedur Aufrufe abrufen. Für Tabellenwert Parameter wird *DataTypePtr* auf SQL_SS_TABLE festgelegt. Zusätzliche Metadaten sind über SQLGetDescField für SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME und SQL_CA_SS_SCHEMA_NAME verfügbar.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME und SQL_CA_SS_SCHEMA_NAME können mit SQLColumns verwendet werden, um Spalten Metadaten für Tabellentypen, die Tabellenwert Parametern zugeordnet sind, abzurufen. In diesem Fall muss SQL_SOPT_SS_NAME_SCOPE auf SQL_SS_NAME_SCOPE_TABLE_TYPE festgelegt werden, bevor SQLColumns aufgerufen wird. SQL_SOPT_SS_NAME_SCOPE sollte wieder auf den Standardwert SQL_SS_NAME_SCOPE_TABLE gesetzt werden, wenn die Anwendung alle Tabellenwertparameter-Spaltenmetadaten abgerufen hat.  
  
 SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME und SQL_CA_SS_SCHEMA_NAME können auch mit CLR-benutzerdefinierten Typparametern verwendet werden.  
  
 Sie können keine Tabellenwertparameter-Metadaten für vorbereitete Anweisungen abrufen, bei denen es sich nicht um gespeicherte Prozeduraufrufe handelt. Wenn Sie dies dennoch versuchen, gibt die Anwendung den Fehler SQL_ERROR mit SQLSTATE 42000 sowie die Meldung "Syntaxfehler oder Zugriffsverletzung" zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwert Parameter &#40;(ODBC)&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
