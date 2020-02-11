---
title: Fehler des Stagingprozesses (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], error messages
ms.assetid: 0d9be0dd-638f-4dd4-92b2-253fda655455
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 65de28bcf880fab6dc0546c5ed4c315978ad39f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65478794"
---
# <a name="staging-process-errors-master-data-services"></a>Fehler des Stagingprozesses (Master Data Services)
  Nach Abschluss des Stagingprozesses verfügen alle in den Stagingtabellen verarbeitete Datensätze über einen Werte in der Spalte ErrorCode. Diese Werte sind in der folgenden Tabelle aufgeführt.  
  
|Code|Fehler|Tritt auf, wenn/Details|Gilt für Tabelle|  
|----------|-----------|--------------------------|----------------------|  
|210001|Der gleiche Elementcode ist in der Stagingtabelle mehrmals vorhanden.|In Ihrer Stagingbatch ist der gleiche Elementcode mehrmals vorhanden. Keines der Elemente wird erstellt oder aktualisiert.|Blatt<br /><br /> Konsolidiert<br /><br /> Beziehung|  
|210003|Die Attributwerte verweisen auf ein Element, das nicht vorhanden oder inaktiv ist.|Wenn Sie domänenbasierte Attribute bereitstellen, müssen Sie den Code und nicht den Namen verwenden. Gilt für **ImportType0**, **1**und **2**.|Blatt<br /><br /> Konsolidiert|  
|210006|Der Elementcode ist inaktiv.|**Importtype** = **1** und Sie haben einen Element Code angegeben, der nicht vorhanden ist.|Blatt<br /><br /> Konsolidiert<br /><br /> Beziehung|  
|210032|Der Hierarchiename fehlt oder ist nicht gültig.|Die explizite Hierarchie wurde nicht gefunden, oder der **HierarchyName** -Wert war leer.|Konsolidiert<br /><br /> Beziehung|  
|210035|Da keine Geschäftsregel zur Codegenerierung vorhanden ist, wird der **MemberCode** benötigt.|Beim Erstellen oder Aktualisieren von Elementen ist ein **MemberCode** immer erforderlich, außer wenn Sie die automatische Codegenerierung verwenden. Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).|Blatt<br /><br /> Konsolidiert|  
|210036|Da eine Geschäftsregel zur Codegenerierung vorhanden ist, wird der **MemberCode** nicht benötigt.|Beim Erstellen oder Aktualisieren von Elementen ist ein **MemberCode** nicht erforderlich, wenn Sie die automatische Codegenerierung verwenden. Sie können jedoch einen Code angeben, wenn Sie dies möchten. Weitere Informationen finden Sie unter [Automatische Codeerstellung &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).|Blatt<br /><br /> Konsolidiert|  
|210041|„ROOT“ ist kein gültiger Elementcode.|Der **MemberCode**-Wert enthält das Wort „ROOT“.|Blatt<br /><br /> Konsolidiert<br /><br /> Beziehung|  
|210042|„MDMUNUSED“ ist kein gültiger Elementcode.|Der **MemberCode**-Wert enthält das Wort „MDMUNUSED“.|Blatt<br /><br /> Konsolidiert<br /><br /> Beziehung|  
|210052|Der MemberCode kann nicht deaktiviert werden, da er als domänenbasierter Attributwert verwendet wird.|Bei **Import Type** = **3** oder **4**schlägt das Staging fehl, wenn der Member als Attribut Wert für andere Elemente verwendet wird. Legen Sie den Wert entweder mithilfe von **ImportType5****6** auf NULL fest, oder ändern Sie die Werte vor dem Ausführen des Stagingprozesses.|Blatt<br /><br /> Konsolidiert|  
|300002|Der Elementcode ist nicht gültig.|Beziehungen: Entweder ist der übergeordnete oder der untergeordnete Elementcode nicht vorhanden.<br /><br /> Blatt oder konsolidiert: **Import Type** = **3** oder **4** und der Element Code ist nicht vorhanden.|Blatt<br /><br /> Konsolidiert<br /><br /> Beziehung|  
|300004|Der Elementcode ist bereits vorhanden.|**Importtype** = **1** und Sie haben einen Element Code verwendet, der bereits in der Entität vorhanden ist.|Blatt<br /><br /> Konsolidiert|  
|210011|Wenn **RelationshipType****1**ist, kann der **ParentCode** kein Blattelement sein.|Stellen Sie sicher, dass der **ParentCode** -Wert ein konsolidierter Elementcode ist.|Beziehung|  
|210015|Der Elementcode für eine Hierarchie und einen Batch ist in der Stagingtabelle mehrmals vorhanden.|Sie haben für eine explizite Hierarchie im gleichen Batch mehrmals den Speicherort des gleichen Elements angegeben.|Beziehung|  
|210016|Die Beziehung konnte nicht erstellt werden, da sie einen Zirkelverweis verursachen würde.|Dieser Fehler tritt auf, wenn Sie versuchen, ein untergeordnetes Element als übergeordnetes Element zuzuweisen.|Beziehung|  
|210046|Das Element kann kein gleichgeordnetes Element von Root sein.|Dies tritt auf, wenn **RelationshipType** = **2** (gleich geordnet) und entweder der **Parametercode** oder **childcode** **root**sind. Elemente können sich nicht auf der gleichen Ebene wie der Stammknoten befinden. Sie können nur untergeordnete Elemente sein.|Beziehung|  
|210047|Das Element kann kein gleichgeordnetes Element von "Nicht verwendet" sein.|Dies tritt auf, wenn **RelationshipType** = **2** (gleich geordnet) und entweder der **Parametercode** oder **childcode** nicht **verwendet**werden. Elemente können nur untergeordnete Elemente des Knotens "Nicht verwendet" sein.|Beziehung|  
|210048|" **Parser Code** " und " **childcode** " dürfen nicht identisch sein.|Der **ParentCode** -Wert ist identisch mit dem **ChildCode** -Wert. Diese Werte müssen unterschiedlich sein.|Beziehung|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen von Fehlern, die während des Stagingprozesses auftreten &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [Daten Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
