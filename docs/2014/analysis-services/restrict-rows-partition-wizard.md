---
title: Einschränken der Zeilen (Partitions-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1b633b19331c836878487920e8145f12aae86f73
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167581"
---
# <a name="restrict-rows-partition-wizard"></a>Zeilen einschränken (Partitions-Assistent)
  Mithilfe der Seite **Zeilen einschränken** können Sie die Zeilen einschränken, die aus der angegebenen Tabelle abgerufen, aggregiert und in die Partition eingeschlossen werden.  
  
> [!NOTE]  
>  Diese Seite wird nur angezeigt, wenn Sie auf der Seite **Quellinformationen angeben** eine einzelne Tabelle ausgewählt haben.  
  
> [!CAUTION]  
>  Wenn Sie auf der Seite **Quellinformationen angeben** unter **Verfügbare Tabellen** eine Tabelle angeben, die auch von einer anderen Partition verwendet wird, müssen Sie auf der Seite **Zeilen einschränken** eine Abfrage bereitstellen, da andernfalls die Gefahr besteht, dass die Daten im Cube dupliziert werden.  
  
## <a name="options"></a>Tastatur  
 **Geben Sie eine Abfrage zum Einschränken der Zeilen**  
 Wählen Sie diese Option aus, um eine Abfrage in das Feld **Abfrage** einzugeben, die die Zeilen einschränkt.  
  
 Wenn beim Auswählen dieser Option das Feld **WHERE-Klausel hinzufügen** leer ist, wird dort eine SQL-Anweisung eingetragen, die alle Spalten und Zeilen aus der zuvor ausgewählten Tabelle abruft.  
  
 **Dataseteigenschaften**  
 Geben Sie die SQL-Anweisung ein, die während der Verarbeitung der Partition zum Abrufen von Zeilen aus der Tabelle verwendet wird, oder ändern Sie diese.  
  
> [!IMPORTANT]  
>  Wenn Sie eine WHERE-Klausel angeben, kann für diese Partition eine Teilmenge von Datensätzen verwendet werden. Dies ist von wesentlicher Bedeutung, um das Duplizieren von Daten zu verhindern, wenn mehrere Partitionen auf einer einzigen Faktentabelle basieren.  
  
 **Check**  
 Überprüft, ob es sich bei der Anweisung in **Abfrage** um eine gültige SQL-Anweisung handelt.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
