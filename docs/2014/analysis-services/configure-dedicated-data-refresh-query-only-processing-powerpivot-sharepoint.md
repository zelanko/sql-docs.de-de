---
title: Konfigurieren der dedizierten Datenaktualisierung oder reinen Abfrageverarbeitung (PowerPivot für SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e027605-1086-4941-bb01-f315df8f829b
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d84528c4d4db768ba58f125e15175604aed7af0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056828"
---
# <a name="configure-dedicated-data-refresh-or-query-only-processing-powerpivot-for-sharepoint"></a>Konfigurieren der dedizierten Datenaktualisierung oder reinen Abfrageverarbeitung (PowerPivot für SharePoint)
  Im integrierten SharePoint-Modus kann eine Analysis Services-Serverinstanz für die Unterstützung bestimmter Verarbeitungsanforderungen wie der Datenaktualisierung oder reinen Abfrageverarbeitung konfiguriert werden. Standardmäßig sind beide Typen von Ladeanforderungen aktiviert. Sie können einen der beiden Typen deaktivieren, um eine dedizierte Abfrage-Engine oder einen Datenaktualisierungsserver zu erstellen.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
> [!NOTE]  
>  In dieser Version gibt es keine Konfigurationseinstellungen zur Begrenzung der Speicherauslastung oder CPU-Nutzung für Datenaktualisierungsaufträge oder bedarfsgesteuerte Abfragen. Eine [!INCLUDE[ssGeminiSrv](../includes/ssgeminisrv-md.md)]-Instanz verwendet alle verfügbaren Ressourcen zur Ausführung der von ihr verwalteten Abfragen und Datenaktualisierungsaufträge.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Konfigurieren eines Verarbeitungsmodus](#config)  
  
 [Ändern der Anzahl von datenaktualisierungsaufträgen, die parallel ausgeführt werden können](#change)  
  
##  <a name="config"></a> Konfigurieren eines Verarbeitungsmodus  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
2.  Klicken Sie oben auf der Seite unter Server auf den Pfeil nach unten und dann auf **Server ändern**.  
  
3.  Wählen Sie den SharePoint-Server mit der zu konfigurierenden Analysis Services-Serverinstanz aus.  
  
4.  Klicken Sie auf **SQL Server Analysis Services**.  
  
5.  Führen Sie unter Verwendung von Dienstinstanzen folgende Schritte aus:  
  
    1.  Deaktivieren Sie das Kontrollkästchen **Laden von schreibgeschützten Datenbanken aktivieren** bedarfsgesteuerte abfrageverarbeitung deaktivieren, das auftritt, wenn ein Benutzer eine Arbeitsmappe öffnet, die PowerPivot-Daten enthält.  
  
    2.  Deaktivieren Sie das Kontrollkästchen **Laden von Datenbanken für die Aktualisierung aktivieren** planmäßige datenaktualisierung deaktivieren.  
  
    > [!NOTE]  
    >  Durch das Deaktivieren der Datenaktualisierung werden keine Datenaktualisierungsoptionen aus SharePoint-Websites entfernt. Besitzer von PowerPivot-Arbeitsmappen können weiterhin Zeitpläne für Datenaktualisierungen erstellen, die Datenaktualisierung wird jedoch auf diesem Server nicht ausgeführt.  
  
6.  Optional können Sie für Datenaktualisierungsvorgänge die Anzahl der gleichzeitigen Aktualisierungsaufträge ändern. Es wird empfohlen, die Anzahl der gleichzeitigen Aufträge zu erhöhen, wenn der Server nur für die Datenaktualisierung konfiguriert ist oder über zusätzliche Prozessoren verfügt. Sie könnten die Anzahl der gleichzeitigen Aufträge verringern, wenn Sie Systemressourcen für zusätzliche bedarfsgesteuerte Abfragen freigeben möchten.  
  
7.  Speichern Sie die Änderungen. Der Server überprüft Ihre Eingaben erst nach Auftreten eines Verarbeitungsereignisses. Wenn Sie für die gleichzeitigen Aufträge einen ungültigen Wert eingeben, wird der Fehler erkannt und bei der Verarbeitung der nächsten Anforderung protokolliert.  
  
##  <a name="change"></a> Ändern der Anzahl von datenaktualisierungsaufträgen, die parallel ausgeführt werden können  
 Ein Datenaktualisierungsauftrag ist ein geplanter Task, der einer von einer PowerPivot-Dienstanwendung verwalteten und überwachten Verarbeitungswarteschlange hinzugefügt wird. Ein Auftrag besteht aus Zeitplaninformationen für eine oder mehrere Datenquellen in einer PowerPivot-Arbeitsmappe. Für jeden definierten Zeitplan wird ein separater Auftrag erstellt. Wenn ein Arbeitsmappenbesitzer einen Zeitplan für alle Datenquellen definiert, wird nur ein Auftrag für den gesamten Datenaktualisierungsvorgang erstellt. Wenn ein Arbeitsmappenbesitzer individuelle Zeitpläne für externe Datenquellen erstellt, werden mehrere Aufträge erstellt und ausgeführt, um eine vollständige Datenaktualisierung für diese Arbeitsmappe durchzuführen.  
  
 Sie können die Anzahl gleichzeitig ausführbarer Datenaktualisierungsaufträge erhöhen, sofern die zusätzliche Last vom System unterstützt wird.  
  
|Einstellung|Gültige Werte|Description|  
|-------------|------------------|-----------------|  
|Standardwert|Berechnet auf Grundlage des RAMs.|Der Standardwert basiert auf dem verfügbaren Arbeitsspeicher geteilt durch 4 GB. Da der Standardwert durch eine Formel berechnet wird, können die Einstellungen abhängig von der Systemkapazität angepasst werden.<br /><br /> Hinweis: Der Divisor von 4 GB wurde auf der Grundlage der RAM-Verwendung für eine umfangreiche Stichprobe realer PowerPivot-Datenquellen ausgewählt. Er basiert nicht auf einer physischen oder logischen PowerPivot-Architektur.|  
|Höchstwert|Berechnet anhand der CPU-Anzahl.|Die maximale Anzahl gleichzeitiger Aufträge, die Sie angeben können, basiert auf der Anzahl von Prozessoren im Computer. Auf einem 4 Socket-Quad-Core-Computer können beispielsweise maximal 16 Aufträge gleichzeitig ausgeführt werden.|  
  
#### <a name="increasing-the-default-value-to-a-higher-value"></a>Heraufsetzen des Standardwerts auf einen höheren Wert  
 Das folgende Diagramm zeigt verschiedene Kombinationen von Arbeitsspeicher (RAM) und CPU. Die resultierenden Standard- und Maximalwerte werden basierend auf den Systemmerkmalen berechnet. Beachten Sie außerdem, dass der berechnete Standardwert für die Anzahl von Datenaktualisierungsaufträgen, die gleichzeitig ausgeführt werden können, auf dem Systemspeicher basiert, während der berechnete maximale Wert auf CPUs basiert. Die letzte Spalte gibt an, ob Sie die maximale Anzahl gleichzeitiger Datenaktualisierungsaufträge heraufsetzen können.  
  
|Effektive RAM-Kapazität (in GB)|Berechneter Standardwert|Effektive CPU-Anzahl|Berechneter Maximalwert|Anzahl gleichzeitiger Aufträge erhöhen?|  
|---------------------------------|------------------------------|------------------------|------------------------------|-------------------------------|  
|4|1|1|1|Nein. Standardwert und Maximalwert sind identisch.|  
|4|1|4|4|Ja. Sie können die Anzahl gleichzeitiger Aufträge auf 2, 3 oder 4 erhöhen.|  
|8|2|4|4|Ja. Sie können die Anzahl gleichzeitiger Aufträge auf 3 oder 4 erhöhen.|  
|16|4|4|4|Nein. Standardwert und Maximalwert sind identisch.|  
|32|Der mit der Formel zum Berechnen des Standardwerts ermittelte Standardwert beträgt 8. Da der Standardwert höher als der zulässige Maximalwert ist, wird der berechnete Standardwert in diesem Fall nicht verwendet.|4|4|Nein. Obwohl die hohe RAM-Kapazität für einen Standardwert von 8 gleichzeitigen Aufträgen sprechen würde, unterstützt ein Computer mit 4 Prozessoren nur maximal 4 gleichzeitige Aufträge.|  
|32|8|8|8|Nein.|  
|32|8|16|16|Ja.|  
|64|16|16|16|Nein.|  
  
 Da es nicht möglich ist, vorauszusagen, ob mehrere Aufträge zur gleichen Zeit erfolgreich ausgeführt werden können, sollten Sie die Anzahl gleichzeitiger Aufträge erst erhöhen, nachdem Sie die Arbeitsspeichernutzung über einen Zeitraum analysiert und festgestellt haben, dass der Serverarbeitsspeicher generell unterausgelastet ist.  
  
 Jeder Datenaktualisierungsauftrag weist andere Auslastungsmerkmale auf, die von der Anzahl und der Größe der aktualisierten Datenquellen abhängig sind. Arbeitsmappen mit einer einzelnen Datenquelle und wenigen Zeilen verursachen eine wesentlich geringere Verarbeitungslast als eine Arbeitsmappe, die zahlreiche Datenquellen und sehr umfangreiche Rowsets aufweist.  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot-Datenaktualisierung mit SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  