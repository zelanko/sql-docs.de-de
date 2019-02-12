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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2ce3283568cebebd81bc98b3d4ebba7ba81d46dd
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041121"
---
# <a name="guidelines-and-limitations-of-diffgrams-in-sqlxml"></a>Richtlinien und Einschränkungen von DiffGrams für SQLXML
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Bei der Verwendung von DiffGrams mit SQLXML 4.0 gilt Folgendes:  
  
-   Binary large Object (BLOB) Typen wie zum Beispiel **Text/Ntext** und Images sollten nicht verwendet werden, der  **\<Diffgr: vor dem >** -block in bei der Verwendung von DiffGrams, da auf diese Weise für die Verwendung in eingeschlossen werden Steuerung der Parallelität. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Z. B. das LIKE-Schlüsselwort werden in der WHERE-Klausel für den Vergleich zwischen den Spalten von der **Text** -Datentyps; Vergleiche schlägt jedoch fehl, im Fall von BLOB-Typen, in denen die Größe der Daten größer als 8 KB ist.  
  
-   Sonderzeichen in **Ntext** Daten können Probleme mit SQLXML 4.0 verursachen, aufgrund der Einschränkungen auf Vergleich für BLOB-Typen. Z. B. die Verwendung von "[Serializable]" in der  **\<Diffgr: vor dem >** -Block eines Diffgrams, bei der Verwendung in der parallelitätsprüfung einer Spalte vom **Ntext** Typ mit der folgenden SQLOLEDB fehl fehlerbeschreibung:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
  
