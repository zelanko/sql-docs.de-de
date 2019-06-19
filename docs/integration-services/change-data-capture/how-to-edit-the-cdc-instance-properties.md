---
title: Bearbeiten der CDC-Instanzeigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9da51ac14564fc7e6a00b7ee9d9f5325073b6b48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65728794"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a>Bearbeiten der CDC-Instanzeigenschaften

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  In diesem Verfahren wird beschrieben, wie Sie die CDC Designer Console verwenden, um die Konfigurationseigenschaften für eine CDC-Instanz zu bearbeiten.  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a>So bearbeiten Sie die Konfigurationseigenschaften einer CDC-Instanz  
  
1.  Wählen Sie im Menü **Start** die Option **CDC Designer Console**aus.  
  
2.  Erweitern Sie im linken Bereich die Option **Change Data Capture** , und erweitern Sie dann den Dienst, der die Instanz mit den zu bearbeitenden Eigenschaften enthält.  
  
3.  Wählen Sie den Namen der Instanz aus, deren Eigenschaften Sie bearbeiten möchten.  
  
4.  Klicken Sie in der der CDC Designer Console rechts im Aktionsbereich auf **Eigenschaften**.  
  
     Sie können auch mit der rechten Maustaste auf die Instanz klicken, für die Sie die Eigenschaften bearbeiten möchten, und dann auf **Eigenschaften**klicken.  
  
5.  Bearbeiten Sie im Eigenschaften-Editor die Eigenschaften auf den folgenden Registerkarten:  
  
    -   **Oracle**: Verwenden Sie im Eigenschaften-Editor die Registerkarte **Oracle**, um Änderungen an der Beschreibung vorzunehmen, die Sie im Assistenten für neue Instanzen auf der Seite „Create CDC database“ angegeben haben, und um Änderungen an den Verbindungsinformationen zur Oracle Log Mining-Datenbank vorzunehmen.  
  
         Informationen zu den Bearbeitungsmöglichkeiten auf dieser Registerkarte finden Sie unter [Edit the Oracle Database Properties](../../integration-services/change-data-capture/edit-the-oracle-database-properties.md).  
  
    -   **Tabellen**: Verwenden Sie die Registerkarte **Tabellen** , um Änderungen an den Tabellen und Spalten vorzunehmen, die Sie in der Oracle-Quelldatenbank ausgewählt haben.  
  
         Informationen zu den Bearbeitungsmöglichkeiten auf dieser Registerkarte finden Sie unter [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
    -   **Skripts**: Verwenden Sie die Registerkarte **Skripts**, um ein Skript für die Oracle-Quelldatenbank auszuführen bzw. erneut auszuführen, mit dem die ergänzende Protokollierung eingerichtet wird.  
  
         Informationen zu den Optionen auf dieser Registerkarte finden Sie unter [Review and Generate Supplemental Logging Scripts](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md).  
  
    -   **Erweitert**: Verwenden Sie die Registerkarte **Erweitert** , um der CDC-Instanz besondere Eigenschaften hinzuzufügen.  
  
         Informationen zu den Optionen auf dieser Registerkarte finden Sie unter [Edit the Advanced Properties](../../integration-services/change-data-capture/edit-the-advanced-properties.md).  
  
  
