---
title: Azure-Blob-Downloadtask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpblobdltask.f1
- sql11.dts.designer.afpblobdltask.f1
ms.assetid: 8a63bf44-71be-456d-9a5c-be7c31aff065
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: af99d5ba79919920b2fb1ff3dde8d0a134a8ef0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62832925"
---
# <a name="azure-blob-download-task"></a>Azure Blob-Download-Task
  Der Azure Blob-Download-Task ermöglicht einem SSIS-Paket das Herunterladen von Dateien aus einem Azure-Blob-Speicher.   
Um einen **Azure Blob-Download-Task**hinzuzufügen, legen Sie ihn mittels Drag &amp; Drop auf dem SSIS-Designer ab, und doppelklicken Sie darauf, oder klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Bearbeiten** , um das folgende Dialogfeld **Azure Blob-Download-Task-Editor** anzuzeigen.  
  
 Die folgende Tabelle enthält Beschreibungen für die Felder in diesem Dialogfeld.  
  
|||  
|-|-|  
|**Feld**|**Beschreibung**|  
|AzureStorageConnection|Geben Sie einen vorhandenen Azure Storage-Verbindungs-Manager an, oder erstellen Sie einen neuen, der sich auf ein Azure-Speicherkonto bezieht, das auf den Speicherort der Blob-Dateien verweist.|  
|BlobContainer|Gibt den Namen des Blob-Containers an, der die herunterzuladenden Blob-Dateien enthält.|  
|BlobDirectory|Gibt das Blob-Verzeichnis an, das die herunterzuladenden Blob-Dateien enthält. Das Blobverzeichnis ist eine virtuelle hierarchische Struktur.|  
|LocalDirectory|Gibt das lokale Verzeichnis an, in dem die heruntergeladenen Blob-Dateien gespeichert werden sollen.|  
|FileName|Gibt einen Namensfilter an, um Dateien mit dem angegebenen Namensmuster auszuwählen. Beispiel: „MeinArbeitsblatt*.xls\* “ schließt „MeinArbeitsblatt001.xls“ und „MeinArbeitsblattABC.xlsx“ ein.|  
|TimeRangeFrom/TimeRangeTo|Gibt einen Zeitbereichsfilter an. Dateien, die nach **TimeRangeFrom** und vor **TimeRangeTo** geändert wurden, sind eingeschlossen.|  
  
  
