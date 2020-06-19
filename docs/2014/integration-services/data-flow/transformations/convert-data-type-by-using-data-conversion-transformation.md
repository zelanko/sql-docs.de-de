---
title: Konvertieren von Daten in einen anderen Datentyp mithilfe der Transformation für Datenkonvertierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 11b381ab7063f44fad9a6505d167d9953b200619
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939671"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a>Konvertieren von Daten in einen anderen Datentyp mithilfe der Transformation für Datenkonvertierung
  Um eine Transformation für Datenkonvertierung hinzuzufügen und zu konfigurieren, muss das Paket bereits mindestens einen Datenflusstask und eine Quelle enthalten.  
  
### <a name="to-convert-data-to-a-different-data-type"></a>So konvertieren Sie Daten in einen anderen Datentyp  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**die Transformation für Datenkonvertierung auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie die Transformation für Datenkonvertierung mit dem Datenfluss, indem Sie einen Konnektor von der Quelle oder der vorherigen Transformation auf die Transformation für Datenkonvertierung ziehen.  
  
5.  Doppelklicken Sie auf die Transformation für Datenkonvertierung.  
  
6.  Aktivieren Sie im Dialogfeld **Transformations-Editor für Datenkonvertierung** in der Tabelle **Verfügbare Eingabespalten** das Kontrollkästchen neben den Spalten, deren Datentyp Sie konvertieren möchten.  
  
    > [!NOTE]  
    >  Für eine Eingabespalte können mehrere Datenkonvertierungen angewendet werden.  
  
7.  Optional können die Standardwerte in der **Ausgabealias** -Spalte geändert werden.  
  
8.  Wählen Sie in der Liste **Datentyp** den neuen Datentyp für die Spalte aus. Der Standarddatentyp ist der Datentyp der Eingabespalte.  
  
9. Aktualisieren Sie optional in Abhängigkeit vom ausgewählten Datentyp die Werte in den Spalten **Länge**, **Genauigkeit**, **Dezimalstellen**und **Codepage** .  
  
10. Um die Fehlerausgabe zu konfigurieren, klicken Sie auf **Fehlerausgabe konfigurieren**. Weitere Informationen finden Sie unter [Konfigurieren einer Fehlerausgabe in einer Datenflusskomponente](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Klicken Sie auf **OK**.  
  
12. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Conversion Transformation](data-conversion-transformation.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../integration-services-paths.md)   
 [SQL Server Integration Services-Datentypen](../integration-services-data-types.md)   
 [Datenflusstask](../../control-flow/data-flow-task.md)  
  
  
