---
title: Updategram-Sicherheitsüberlegungen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 22dbfec9d0be8e08f816d28b310df3025918724a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096070"
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Sicherheitsüberlegungen zu Updategrams (SQLXML 4.0)
  Im Folgenden finden Sie Sicherheitsrichtlinien zur Verwendung von Updategrams:  
  
-   Vermeiden Sie die Verwendung von Standardzuordnungen, wenn Sie Daten mithilfe von Updategrams aktualisieren. Bei Verwendung einer Standardzuordnung wird einem Elementnamen in einem Updategram ein Tabellenname und einem Attributnamen wird eine Spalte zugeordnet. Dadurch werden die Datentabelle und die Spaltendaten der Datenbank verfügbar gemacht, und dies kann potenziell ein Sicherheitsrisiko darstellen. Wenn Sie stattdessen ein eigenes Zuordnungsschema angeben, um die Elemente und Attribute eines Updategrams den Datenbanktabellen und –spalten zuzuordnen, dann können Sie für das Updategram beliebige Element- und Attributnamen wählen und dem Schema die Zuordnung dieser Namen zu Datenbanktabellen und –spalten überlassen. So werden die Datenbankinformationen nicht in einem Updategram verfügbar gemacht.  
  
-   Lassen Sie nicht zu, dass Benutzer eigene Updategrams erstellen und ausführen. Updategrams sollten sich in Form von Vorlagen auf dem Server befinden und nicht mithilfe von Anwendungen im ASP-Stil dynamisch erstellt werden, da sonst die Daten der Datenbank gefährdet werden könnten. Dieses Risiko lässt sich ausschließen, indem Benutzer lediglich erlaubt wird, über die als Vorlagen bereitgestellten Updategrams auf die Daten zuzugreifen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Updategramms zum Ändern von Daten in SQLXML 4.0](../updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
