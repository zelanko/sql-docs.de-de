---
title: Transformations-Editor für Union all | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7e84c106767aa897b2e419b51ca5b5c538501cf
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420337"
---
# <a name="union-all-transformation-editor"></a>Transformations-Editor für UNION ALL
  Mithilfe des Dialogfelds **Transformations-Editor für UNION ALL** können Sie mehrere Eingaberowsets zu einem einzigen Ausgaberowset zusammenführen. Durch das Einschließen der Transformation für UNION ALL in einen Datenfluss können Sie Daten aus mehreren Datenflüssen zusammenführen, komplexe Datasets durch Verschachteln der Transformationen für UNION ALL erstellen und Zeilen erneut zusammenführen, nachdem Sie Fehler in den Daten korrigiert haben.  
  
 Weitere Informationen zur Transformation für UNION ALL finden Sie unter [Union All Transformation](data-flow/transformations/union-all-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Name der Ausgabespalte**  
 Geben Sie einen Alias für jede Spalte ein. Standardmäßig wird der Name der Eingabespalte von der ersten (Referenz-)Eingabe verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
 **Eingabe 1 für UNION ALL**  
 Wählen Sie eine Eingabespalte aus der Liste der verfügbaren Eingabespalten in der ersten (Referenz-)Eingabe aus. Die Metadaten der zugeordneten Spalten müssen übereinstimmen.  
  
 **Eingabe n für UNION ALL**  
 Wählen Sie eine Eingabespalte aus der Liste der verfügbaren Eingabespalten in den folgenden Eingaben aus. Die Metadaten der zugeordneten Spalten müssen übereinstimmen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Zusammenführen von Daten mithilfe der Transformation für Union all](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md)   
 [Transformation für Zusammenführen](data-flow/transformations/merge-transformation.md)   
 [Transformation für Zusammenführungsjoin](data-flow/transformations/merge-join-transformation.md)  
  
  
