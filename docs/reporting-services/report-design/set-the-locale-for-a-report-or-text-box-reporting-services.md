---
title: Festlegen des Gebietsschemas für einen Bericht oder ein Textfeld (Reporting Services) | Microsoft-Dokumentation
description: Mithilfe der Spracheigenschaft eines Textfelds können Sie im Berichts-Generator das Gebietsschema für Formate konfigurieren, die Daten anzeigen, die sich hinsichtlich der Sprache und der Region unterscheiden.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- locales [Reporting Services]
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4105c10fba6774275471a1157677badf88c11f5f
ms.sourcegitcommit: e572f1642f588b8c4c75bc9ea6adf4ccd48a353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2020
ms.locfileid: "84779093"
---
# <a name="set-the-locale-for-a-report-or-text-box-reporting-services"></a>Festlegen des Gebietsschemas für einen Bericht oder ein Textfeld (Reporting Services)
  Die **Language** -Eigenschaft eines Berichts oder eines Textfelds enthält das Gebietsschema, das die Standardformate zur Anzeige von Berichtsdaten festlegt, die je nach Land unterschiedlich sind, z. B. bei Datums-, Währungs- oder Zahlwerten. Die **Language** -Eigenschaft eines Textfelds hat Vorrang vor der **Language** -Eigenschaft des Berichts. Wenn für **Language**kein Wert angegeben wird, verwendet Reporting Services das Gebietsschema des Betriebssystems auf dem Berichtsserver für veröffentlichte Berichte oder auf dem Computer zur Berichterstellung für die Berichtsvorschau.  
  
 Bei HTML-Berichten können Sie den Standardwert der **Language** -Eigenschaft überschreiben und die über den HTTP-Header des Browser-Clients angegebene Sprache verwenden, indem Sie das eingebettete Feld „User!Language“ in einem Ausdruck für die **Language** -Eigenschaft eines Berichts bzw. eines Textfelds verwenden.  
  
 Außerdem können Sie die **Language** -Eigenschaft für einen Bericht in einer URL angeben. Weitere Informationen finden Sie unter [Festlegen der Sprache für Berichtsparameter in einer URL](../../reporting-services/set-the-language-for-report-parameters-in-a-url.md).  
  
### <a name="to-set-the-locale-for-a-report"></a>So legen Sie das Gebietsschema für einen Bericht fest  
  
1.  Klicken Sie in der Entwurfssicht auf eine Stelle außerhalb der Berichts-Entwurfsoberfläche, um den Bericht auszuwählen.  
  
2.  Geben Sie im Eigenschaftenbereich für die **Language** -Eigenschaft die Sprache ein, die Sie für den Bericht verwenden möchten, oder wählen Sie sie aus.  
  
### <a name="to-set-the-locale-for-a-text-box"></a>So legen Sie das Gebietsschema für ein Textfeld fest  
  
1.  Wählen Sie in der Entwurfssicht das Textfeld aus, für das die Gebietsschemaeinstellungen übernommen werden sollen.  
  
2.  Führen Sie im Eigenschaftenbereich folgende Schritte aus:  
  
    -   Geben Sie für die **Calendar** -Eigenschaft den Kalender ein, der für Datumsangaben verwendet werden soll, oder wählen Sie ihn aus.  
  
    -   Geben Sie für die **Direction** -Eigenschaft die Schreibrichtung für den Text ein, oder wählen Sie sie aus.  
  
    -   Geben Sie für die **Language** -Eigenschaft die Sprache ein, die für das Textfeld verwendet werden soll, oder wählen Sie sie aus. Dieser Wert überschreibt die **Language** -Eigenschaft des Berichts.  
  
    -   Geben Sie für die **NumeralLanguage** -Eigenschaft das Format für Zahlen im Textfeld ein, oder wählen Sie es aus.  
  
    -   Geben Sie für die **NumeralVariant** -Eigenschaft die zu verwendende Variante für das Zahlenformat im Textfeld ein, oder wählen Sie sie aus.  
  
    -   Wählen Sie für die **UnicodeBiDi** -Eigenschaft den bidirektionalen Einbettungsgrad aus, der für das Textfeld verwendet werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Überlegungen zu Lösungsentwürfen für mehrsprachige oder globale Bereitstellungen (Reporting Services)](https://msdn.microsoft.com/55630eca-d1e5-4ac6-93c7-9a3f15c0d08a)  
  
  
