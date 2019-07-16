---
title: Parametrisierte Befehle mit dazwischen liegenden COMPUTE-Befehlen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb6bc2b9f7e53caf28f44daf39815850940b9d3a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924726"
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>Parametrisierte Befehle mit dazwischen liegenden COMPUTE-Befehlen
Eine typische parametrisierte Form APPEND-Befehl hat eine Klausel, die ein übergeordnetes Element erstellt **Recordset** mit einem Abfragebefehl und eine weitere Klausel, die ein untergeordnetes Element erstellt **Recordset** mit einem parametrisierten Abfrage-Befehl: d. h. einen Befehl mit einem Platzhalter für Parameter (ein Fragezeichen, "?"). Das resultierende strukturierte **Recordset** hat zwei Ebenen, in dem das übergeordnete Element die obere Ebene belegt, und das untergeordnete Element belegt die untere Ebene.  
  
 Die Klausel, die das untergeordnete Element erstellt **Recordset** nun möglicherweise eine beliebige Anzahl von geschachtelten Shape COMPUTE-Befehle, die am tiefsten geschachtelte Befehl, in denen die parametrisierte Abfrage enthält. Das resultierende strukturierte **Recordset** verfügt über mehrere Ebenen aufweist, in dem das übergeordnete Element die oberste Ebene belegt, das untergeordnete Element nimmt die unterste Ebene und eine beliebige Anzahl von **Recordset**s generiert, indem Sie die Shape COMPUTE-Befehlen, die dazwischen liegenden Ebenen beanspruchen.  
  
 Die typische Verwendung für diese Funktion ist, die aggregate-Funktion und Gruppierungsfunktionen von ShapeCOMPUTE aufzurufen. Befehle zum Erstellen der dazwischen liegenden **Recordset** Objekten mit analytischen Informationen über das untergeordnete Element **Recordset** . Darüber hinaus da es sich um einen Befehl für die parametrisierte Form handelt, jedes Mal eine Kapitelspalte des übergeordneten Elements erfolgt, eine neue untergeordnete **Recordset** abgerufen werden kann. Da die dazwischen liegenden Ebenen von untergeordneten abgeleitet werden, werden sie auch neu berechnet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Shaping Example (Beispiele der Datenstrukturierung)](../../../ado/guide/data/data-shaping-example.md)
