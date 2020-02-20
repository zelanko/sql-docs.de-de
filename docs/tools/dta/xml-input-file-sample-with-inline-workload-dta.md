---
title: Beispiel für eine XML-Eingabedatei mit Inlinearbeitsauslastung
titleSuffix: DTA
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: b12c6f285a7c9eb1e32c33332b00ec624092c3c6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75258020"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a>Beispiel für eine XML-Eingabedatei mit Inlinearbeitsauslastung (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Kopieren Sie dieses Beispiel für eine XML-Eingabedatei, die eine Arbeitsauslastung mit dem **EventString** -Element angibt, und fügen Sie sie in Ihren XML-Editor oder Text-Editor ein. Mit dem **EventString** -Element können Sie eine auf einem [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript basierende Arbeitsauslastung in der XML-Eingabedatei angeben, anstatt eine separate Arbeitsauslastungsdatei zu verwenden. Nach dem Kopieren dieses Beispiels in Ihr Bearbeitungstool ersetzen Sie die Werte für das **Server**-, **Database**-, **Schema**-, **Table**-, **Workload**-, **EventString**- und **TuningOptions** -Element durch die Werte für Ihre Optimierungssitzung. Weitere Informationen zu sämtlichen Attributen und untergeordneten Elementen, die Sie zusammen mit diesen Elementen verwenden können, finden Sie unter [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md). Im folgenden Beispiel wird nur eine Teilmenge der verfügbaren Optionen für Attribute und untergeordnete Elemente verwendet.

## <a name="code"></a>Code

[!code-xml[InputFileSamples#InlineWorkloadInputFile](../../tools/dta/codesnippet/xml/xml-input-file-sample-wi_1.xml)]

## <a name="comments"></a>Kommentare

`USE database_name` -Anweisungen können in der Inlinearbeitsauslastung angegeben werden, die im **EventString** -Element enthalten ist.

## <a name="see-also"></a>Weitere Informationen

- [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)
- [Anzeigen und Verwenden der Ausgabe des Datenbankoptimierungsratgebers](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)
- [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)