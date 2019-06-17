---
title: Transformation für OLE DB-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbcommandtrans.f1
helpviewer_keywords:
- statements [Integration Services]
- OLE DB Command transformation
ms.assetid: baa6735c-5acf-4759-b077-1216aca16c6c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3a8ffc33de161c71c6f72eebf8616d1e814fb994
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62770387"
---
# <a name="ole-db-command-transformation"></a>Transformation für OLE DB-Befehl
  Die Transformation für OLE DB-Befehl führt eine SQL-Anweisung für jede Zeile in einem Datenfluss aus. Beispielsweise können Sie eine SQL-Anweisung ausführen, die Zeilen in einer Datenbanktabelle einfügt, aktualisiert oder löscht.  
  
 Es gibt folgende Möglichkeiten, um die Transformation für OLE DB-Befehl zu konfigurieren:  
  
-   Stellen Sie die SQL-Anweisung bereit, die die Transformation für jede Zeile ausführt.  
  
-   Geben Sie an, nach wie vielen Sekunden ein Timeout bei der SQL-Anweisung eintritt.  
  
-   Geben Sie die Standardcodepage an.  
  
 In der Regel enthält die SQL-Anweisung Parameter. Die Parameterwerte sind in externen Spalten in der Transformationseingabe gespeichert, und beim Zuordnen einer Eingabespalte zu einer externen Spalte wird eine Eingabespalte einem Parameter zugeordnet. Angenommen, Sie möchten Zeilen in der **DimProduct** -Tabelle anhand des Werts in der **ProductKey** -Spalte suchen und diese dann löschen. Hierzu können Sie die externe Spalte **Param_0** der **ProductKey** -Eingabespalte zuordnen und anschließend den SQL-Befehl `DELETE FROM DimProduct WHERE ProductKey = ?`ausführen. Die Transformation für OLE DB-Befehl stellt die Parameternamen bereit, die nicht geändert werden können. Die Parameternamen lauten **Param_0**, **Param_1**usw.  
  
 Wenn Sie die Transformation für OLE DB-Befehl mithilfe des Dialogfelds **Erweiterter Editor** konfigurieren, können die Parameter in der SQL-Anweisung automatisch externen Spalten in der Transformationseingabe zugeordnet und die Merkmale jedes Parameters definiert werden, indem Sie auf die Schaltfläche **Aktualisieren** klicken. Wenn jedoch der von der Transformation für OLE DB-Befehl verwendete OLE DB-Anbieter das Ableiten von Parameterinformationen von dem Parameter nicht unterstützt, müssen Sie die externen Spalten manuell konfigurieren. Das heißt, Sie müssen der Transformation für jeden Parameter zur externen Eingabe eine Spalte hinzufügen, die Spaltennamen aktualisieren, um Namen wie **Param_0**zu verwenden, den Wert der DBParamInfoFlags-Eigenschaft angeben sowie die Eingabespalten, die Parameterwerte enthalten, den externen Spalten zuordnen.  
  
 Der Wert von DBParamInfoFlags stellt die Merkmale des Parameters dar. Beispielsweise gibt der Wert **1** an, dass der Parameter ein Eingabeparameter ist, und der Wert **65** gibt an, dass der Parameter ein Eingabeparameter ist und einen NULL-Wert enthalten kann. Die Werte müssen mit den Werten in der OLE DB-Enumeration DBPARAMFLAGSENUM übereinstimmen. Weitere Informationen finden Sie in der OLE DB-Referenzdokumentation.  
  
 Die Transformation für OLE DB-Befehl schließt die benutzerdefinierte Eigenschaft `SQLCommand` ein. Diese Eigenschaft kann beim Laden des Pakets mithilfe eines Eigenschaftsausdrucks aktualisiert werden. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md), [Verwenden von Eigenschaftsausdrücken in Paketen](../../expressions/use-property-expressions-in-packages.md) und [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md).  
  
 Diese Transformation weist eine Eingabe, eine reguläre Ausgabe und eine Fehlerausgabe auf.  
  
## <a name="logging"></a>Protokollierung  
 Sie können die von der Transformation für OLE DB-Befehl an externe Datenanbieter gerichteten Aufrufe protokollieren. Mithilfe dieser Protokollierungsfunktion können Sie Probleme bei Verbindungen mit externen Datenquellen und bei Befehlen an externe Datenquellen durch die Transformation für OLE DB-Befehl behandeln. Aktivieren Sie zum Protokollieren der von der Transformation für OLE DB-Befehl an externe Datenanbieter gerichteten Aufrufe die Paketprotokollierung, und wählen Sie das **Diagnostic** -Ereignis auf Paketebene aus. Weitere Informationen finden Sie unter [Behandeln von Problemen mit Paketausführungstools](../../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Sie können die Transformation konfigurieren, indem Sie entweder den [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder das Objektmodell verwenden. Details zur Konfiguration der Transformation mithilfe des [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designers finden Sie unter  [Konfigurieren der Transformation für OLE DB-Befehl](../../configure-the-ole-db-command-transformation.md). Details zum programmgesteuerten Konfigurieren dieser Transformation finden Sie im Entwicklerhandbuch.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
