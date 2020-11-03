---
title: Beibehalten der Datumsformatierung für Analysis Services in mobilen Berichten | Reporting Services | Microsoft-Dokumentation
description: Fügen Sie im Publisher für mobile Berichte ein Measure zu einem freigegebenen Dataset im Berichts-Generator hinzu, damit Datumsangaben in Analysis Services-Datenquellen ihren Datentyp beibehalten.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: e9a9a199-40e3-4381-b250-1b99fb83aa62
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5fef66452820975107e06e20a4085978163d957d
ms.sourcegitcommit: ea0bf89617e11afe85ad85309e0ec731ed265583
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907082"
---
# <a name="retain-date-formatting-for-analysis-services-in-mobile-reports"></a>Beibehalten der Datumsformatierung für Analysis Services in mobilen Berichten
Fügen Sie im Berichts-Generator einem freigegebenen Dataset ein Measure so hinzu, dass Datumsangaben in [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] -Datenquellen ihren Datentyp in [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)]beibehalten.

Der Standardrückgabetyp für [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] -Abfragen ist eine Zeichenfolge.  Beim Erstellen eines Datasets im Berichts-Generator von [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] wird der „string“-Datentyp berücksichtigt und auf dem Server gespeichert. 

Wenn jedoch der JSON-Tabellenrenderer das Dataset verarbeitet, liest er den Wert der Spalte als Zeichenfolge und rendert Zeichenfolgen.  Wenn dann [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)] die Tabelle abruft, werden auch nur Zeichenfolgen angezeigt.

Um dieses Problem zu umgehen, fügen Sie ein berechnetes Element hinzu, wenn Sie im Berichts-Generator ein freigegebenes Dataset erstellen. Dies funktioniert für mehrdimensionale und tabellarische [!INCLUDE[ssASnoversion_md](../../includes/ssasnoversion-md.md)] -Modelle.

## <a name="create-a-measure-to-retain-a-date-field-data-type"></a>Erstellen eines Measures zum Beibehalten des Datentyps des Datumsfelds

1. Erstellen Sie ein Measure zum Aufnehmen des Werts des betreffenden Datumsfelds. Wählen Sie im Ausdrucksfeld die Hierarchie/Stufe des Datums, und fügen Sie **.CurrentMember.MemberValue** an. Beispiel:
 
   [Internet Sales].[Ship Date].CurrentMember.MemberValue
   
   ![Screenshot des Dialogfelds „Generator für berechnete Elemente“, in dem das Textfeld „Ausdruck“ hervorgehoben ist](../../reporting-services/mobile-reports/media/ssas-calculated-member-report-builder.png)
   
2. Sie können nun dieses berechnete Element an die Gruppe der Spalten anfügen, indem Sie es aus der Liste „Berechnete Elemente“ links unten ziehen und im Spaltenraster rechts ablegen.  

   ![Screenshot des Abfrage-Designers mit hervorgehobenem Abschnitt „Berechnete Elemente“](../../reporting-services/mobile-reports/media/ssas-query-designer-calculated-member-report-builder.png) 
   
### <a name="see-also"></a>Weitere Informationen

-  [Data for Reporting Services mobile reports (Daten für mobile Berichte von Reporting Services)](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md)
-  [Prepare data for Reporting Services mobile reports (Vorbereiten von Daten für mobile Berichte von Reporting Services)](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
