---
title: Tabellenwertparameter-Metadaten für vorbereitete Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43ef41affecd131626da17ec7d608249437abed6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210610"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>Tabellenwertparameter-Metadaten für vorbereitete Anweisungen
  Eine Anwendung kann Metadaten für einen vorbereiteten Prozeduraufruf SQLNumParams und SQLDescribeParam abrufen. Für Tabellenwertparameter *DataTypePtr* auf SQL_SS_TABLE festgelegt wird. Zusätzliche Metadaten sind über SQLGetDescField für SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME und SQL_CA_SS_SCHEMA_NAME verfügbar.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME und SQL_CA_SS_SCHEMA_NAME können mit SQLColumns verwendet werden, um Spaltenmetadaten für Tabellentypen mit Tabellenwertparametern zu erhalten. In diesem Fall muss SQL_SOPT_SS_NAME_SCOPE auf SQL_SS_NAME_SCOPE_TABLE_TYPE festgelegt werden, bevor SQLColumns aufgerufen wird. SQL_SOPT_SS_NAME_SCOPE sollte wieder auf den Standardwert SQL_SS_NAME_SCOPE_TABLE gesetzt werden, wenn die Anwendung alle Tabellenwertparameter-Spaltenmetadaten abgerufen hat.  
  
 SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME und SQL_CA_SS_SCHEMA_NAME können auch mit CLR-benutzerdefinierten Typparametern verwendet werden.  
  
 Sie können keine Tabellenwertparameter-Metadaten für vorbereitete Anweisungen abrufen, bei denen es sich nicht um gespeicherte Prozeduraufrufe handelt. Wenn Sie dies dennoch versuchen, gibt die Anwendung den Fehler SQL_ERROR mit SQLSTATE 42000 sowie die Meldung "Syntaxfehler oder Zugriffsverletzung" zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
