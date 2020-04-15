---
title: SQLTables (Textdateitreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 938ceba5da25d176628d5c1d9875383d977e3aec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299330"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält Textdateitreiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *szTableOwner* ist NULL, da keine der Treiber Besitzernamen unterstützt. Wenn *szTableOwner* auf NULL gesetzt ist, werden alle Tabellen zurückgegeben. NULL wird in der Spalte TABLE_OWNER zurückgegeben.|  
|*szTableQualifier*|In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad in ein Verzeichnis zurück.|  
|*SzTableType*|"TABLE" ist der einzige unterstützte Tabellentyp.<br /><br /> Wenn der Texttreiber verwendet wird, wird die Liste der von **SQLTables** zurückgegebenen Dateien durch die Dateierweiterungen im Feld **Erweiterungenliste** im Dialogfeld **ODBC-Textsetup** bestimmt.|
