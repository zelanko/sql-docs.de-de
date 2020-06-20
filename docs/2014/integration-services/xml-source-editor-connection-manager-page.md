---
title: Quellen-Editor für XML (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: janinezhang
ms.author: janinez
ms.openlocfilehash: e0df8c4cf72574df16ad42445434592faeae8548
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972370"
---
# <a name="xml-source-editor-connection-manager-page"></a>Quellen-Editor für XML (Seite Verbindungs-Manager)
  Mithilfe der Seite **Verbindungs-Manager** in **Quellen-Editor für XML** können Sie eine XML-Datei und die XML-Schemadefinition (XSD) angeben, mit der die XML-Daten transformiert werden.  
  
 Weitere Informationen zur XML-Quelle finden Sie unter [XML Source](data-flow/xml-source.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Datenzugriffs Modus**  
 Geben Sie die Methode für die Auswahl von Daten aus der Quelle an.  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|XML-Dateispeicherort|Ruft Daten aus einer XML-Datei ab.|  
|XML-Datei aus Variable|Gibt den XML-Dateinamen in einer Variablen an.<br /><br /> **Verwandte Informationen:**[Verwenden von Variablen in Paketen](../../2014/integration-services/use-variables-in-packages.md)|  
|XML-Daten aus Variable|Ruft XML-Daten aus einer Variablen ab.|  
  
 **Inlineschema verwenden**  
 Gibt an, ob die XML-Quelldaten das XSD-Schema enthalten, mit dem die Struktur und die Daten definiert und überprüft werden.  
  
 **XSD-Speicherort**  
 Geben Sie den Pfad und den Dateinamen der XSD-Schemadatei ein, oder suchen Sie die Datei, indem Sie auf die Schaltfläche **Durchsuchen**klicken.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie die XSD-Schemadatei suchen.  
  
 **XSD-Code generieren**  
 Mithilfe des Dialogfelds **Speichern unter** können Sie einen Speicherort für die automatisch generierte XSD-Schemadatei auswählen. Der Editor leitet das Schema aus der Struktur der XML-Daten ab.  
  
## <a name="data-access-mode-dynamic-options"></a>Dynamische Optionen (Datenzugriffsmodus)  
  
### <a name="data-access-mode--xml-file-location"></a>Datenzugriffsmodus = Speicherort der XML-Datei  
 **XML-Speicherort**  
 Geben Sie den Pfad und den Dateinamen der XML-Datendatei ein, oder suchen Sie die Datei, indem Sie auf die Schaltfläche **Durchsuchen**klicken.  
  
 **Durchsuchen**  
 Mithilfe des Dialogfelds **Öffnen** können Sie die XML-Datendatei suchen.  
  
### <a name="data-access-mode--xml-file-from-variable"></a>Datenzugriffsmodus = XML-Datei aus Variable  
 **Variablenname**  
 Wählt die Variable aus, die den Pfad und den Dateinamen der XML-Datei enthält.  
  
### <a name="data-access-mode--xml-data-from-variable"></a>Datenzugriffsmodus = XML-Daten aus Variable  
 **Variablenname**  
 Wählt die Variable aus, die die XML-Daten enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Der Quellen-Editor für XML-&#40;Spalten&#41;](../../2014/integration-services/xml-source-editor-columns-page.md)   
 [Quellen-Editor für XML-&#40;Seite Fehlerausgabe&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md)   
 [Extrahieren von Daten mithilfe der XML-Quelle](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
