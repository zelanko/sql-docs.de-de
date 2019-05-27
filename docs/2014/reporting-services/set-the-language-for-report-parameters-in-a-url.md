---
title: Festlegen der Sprache für Berichtsparameter in einer URL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8087a181906517bb60d4cd6839eed0681f52a5eb
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66101331"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a>Festlegen der Sprache für Berichtsparameter in einer URL
  Der *rs:ParameterLanguage* -Parameter für den URL-Zugriff behebt ein Problem, das auftritt, wenn kulturabhängige Berichtsparameter wie Datums-, Zeit-, Währungs- und Zahlenangaben über die Spracheinstellung des Browsers interpretiert werden. Mit *rs:ParameterLanguage*wird die URL unabhängig vom Browser interpretiert. Wenn die Ländereinstellungen des Berichtsservers z. B. auf die Option Deutsch festgelegt sind, ein Benutzer jedoch mit einem Browser, für den die Option Englisch festgelegt ist, über eine URL auf einen Bericht zugreift, werden die an den Berichtsserver übergebenen Parameterwerte falsch interpretiert.  
  
 Betrachten Sie die folgende URL für einen Bericht:  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 Im oben beschriebenen Fall generiert der Server, der unter der Kultur "de-de" ausgeführt wird, eine URL entweder durch ein E-Mail-Abonnement oder durch einen Link. Der Link gibt an, dass der Bericht gemäß deutschen Standards für Datums- und Zeitangaben mit dem 4. Oktober 2008 als Anfangsdatum und dem 11. Oktober 2008 als Enddatum parametrisiert werden soll. Ein Benutzer, der mit einem Browser auf die URL zugreift, für den die Option "en-us" festgelegt wurde, zwingt den Server, die Werte gemäß amerikanischen Standards für Datums- und Zeitangaben als 10. April 2008 und 10. November 2008 zu interpretieren. Das Problem kann behoben werden, indem Sie mit *rs:ParameterLanguage* die Browsersprache für die Parameterinterpretation überschreiben:  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 Zusätzlich zu den Werten **true** und **false** für den URL-Zugriffsparameter *rc:Parameters*können Sie jetzt den Wert **Collapsed**übergeben. Wenn Sie *rc:Parameters*=**Collapsed** für eine URL verwenden, wird der Eingabeaufforderungsbereichs für Parameter des HTML-Viewers ausgeblendet, kann jedoch vom Benutzer wieder eingeblendet werden. Der Wert **false** entfernt den Eingabeaufforderungsbereichs für Parameter ganz aus der Symbolleiste des HTML-Viewers, und der Endbenutzer kann den Parameterbereich nicht mehr anzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL-Zugriffsparameterverweis](url-access-parameter-reference.md)  
  
  
