---
title: Richtlinien und Einschränkungen von DiffGrams für SQLXML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: cf8689c4-2a63-4d05-b202-21b5ff187d7f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d30c7a93906f9de5fb3826ac4d8a8e1f845f1693
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47779168"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Richtlinien und Einschränkungen von DiffGrams für SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Bei der Verwendung von DiffGrams mit SQLXML 4.0 gilt Folgendes:  
  
-   Binary large Object (BLOB) Typen wie zum Beispiel **Text/Ntext** und Images sollten nicht verwendet werden, der  **\<Diffgr: vor dem >** -block in bei der Verwendung von DiffGrams, da auf diese Weise für die Verwendung in eingeschlossen werden Steuerung der Parallelität. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Z. B. das LIKE-Schlüsselwort werden in der WHERE-Klausel für den Vergleich zwischen den Spalten von der **Text** -Datentyps; Vergleiche schlägt jedoch fehl, im Fall von BLOB-Typen, in denen die Größe der Daten größer als 8 KB ist.  
  
-   Sonderzeichen in **Ntext** Daten können Probleme mit SQLXML 4.0 verursachen, aufgrund der Einschränkungen auf Vergleich für BLOB-Typen. Z. B. die Verwendung von "[Serializable]" in der  **\<Diffgr: vor dem >** -Block eines Diffgrams, bei der Verwendung in der parallelitätsprüfung einer Spalte vom **Ntext** Typ mit der folgenden SQLOLEDB fehl fehlerbeschreibung:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
