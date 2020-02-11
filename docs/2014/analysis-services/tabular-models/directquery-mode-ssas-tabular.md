---
title: Directquery-Modus (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.realtime.f1
ms.assetid: 45ad2965-05ec-4fb1-a164-d8060b562ea5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9a9c1510030f61896f686b49f4bc134a7dfcb42b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67284872"
---
# <a name="directquery-mode-ssas-tabular"></a>DirectQuery-Modus (SSAS – tabellarisch)
  Analysis Services ermöglicht das Abrufen von Daten und das Erstellen von Berichten aus einem tabellarischen Modell, indem Daten und Aggregate direkt aus einem relationalen Datenbanksystem mithilfe des *directquery-Modus*abgerufen werden. In diesem Thema werden die Unterschiede zwischen standardmäßigen Tabellenmodellen erläutert, die sich nur in Arbeitsspeicher- und Tabellenmodellen befinden, die eine relationale Datenquelle abfragen können. Zudem wird erklärt, wie Sie Modelle für die Verwendung im DirectQuery-Modus entwerfen und bereitstellen können.  
  
 Abschnitte in diesem Thema:  
  
-   [Vorteile des DirectQuery-Modus](#bkmk_Benefits)  
  
-   [Erstellen von Modellen zur Verwendung mit DirectQuery-Modus](#bkmk_Design)  
  
    -   [Datenquellen für DirectQuery-Modelle](directquery-mode-ssas-tabular.md#bkmk_DataSources)  
  
    -   [Validierungs- und Entwurfsbeschränkungen für den DirectQuery-Modus](#bkmk_Validation)  
  
    -   [Formelkompatibilität für DirectQuery-Modelle](#bkmk_FormulaCompat)  
  
    -   [Sicherheit im DirectQuery-Modus](#bkmk_Security)  
  
    -   [Sicherheit im DirectQuery-Modus](#bkmk_Security)  
  
-   [DirectQuery-Eigenschaften](#bkmk_PropertyList)  
  
-   [Verwandte Themen und Tasks](#bkmk_related_tasks)  
  
##  <a name="bkmk_Benefits"></a>Vorteile des directquery-Modus  
 Standardmäßig verwenden Tabellenmodelle einen Cache im Arbeitsspeicher, um Daten zu speichern und abzufragen. Da diese Tabellenmodelle Daten verwenden, die sich im Arbeitsspeicher befinden, können auch komplexe Abfragen äußerst schnell ausgeführt werden. Die Verwendung zwischengespeicherter Daten ist jedoch auch mit einigen Nachteilen verbunden:  
  
-   Daten werden nicht aktualisiert, wenn sich die Quelldaten ändern. Sie müssen das Modell verarbeiten, um die Daten zu aktualisieren.  
  
-   Wenn Sie den Computer ausschalten, der das Modell hostet, wird der Cache auf der Festplatte gespeichert und muss erneut geöffnet werden, wenn das Modell geladen oder die PowerPivot-Datei geöffnet wird. Die Speicher- und Ladevorgänge können zeitaufwändig sein.  
  
 Im Gegensatz dazu verwendet der DirectQuery-Modus Daten, die in einer SQL Server-Datenbank gespeichert werden.  Im Allgemeinen werden während der Modellerstellung alle oder ein kleiner Teil der Daten in den Cache importiert. Wenn das Modell bereitgestellt wird, geben Sie an, dass als Datenquelle für Abfragen des Modells anstelle der zwischengespeicherten Daten SQL Server verwendet werden soll. Alle DAX-Abfragen der Daten werden von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die angegebene relationale Datenquelle in entsprechende SQL-Anweisungen übersetzt.  
  
 Es ergeben sich zahlreiche Vorteile aus der Bereitstellung von Modellen mit dem DirectQuery-Modus:  
  
-   Es kann vorkommen, dass die Datasets für ein Modell zu groß für den Arbeitsspeicher auf dem Analysis Services-Server sind.  
  
-   Die Daten sind in jedem Fall aktuell, und es entsteht kein zusätzlicher Verwaltungsaufwand für die Verwaltung einer separaten Kopie der Daten. Änderungen an den zugrunde liegenden Quelldaten werden umgehend in Abfragen des Datenmodells sichtbar.  
  
-   DirectQuery kann die Abfragebeschleunigung des Anbieters nutzen, z. B. die entsprechende Funktion von speicheroptimierten xVelocity-Spaltenindizes.  
  
-   Jede Sicherheitsmaßnahme, die von der Back-End-Datenbank erzwungen wird, wird in jedem Fall mithilfe von Sicherheit auf Zeilenebene erzwungen. Wenn Sie dagegen zwischengespeicherte Daten verwenden, lässt sich nur schwer sicherstellen, dass der Zwischenspeicher exakt entsprechend dem Server gesichert wird.  
  
-   Wenn das Modell komplexe Formeln enthält, die unter Umständen mehrere Abfragen erfordern, kann Analysis Services eine Optimierung ausführen, um sicherzustellen, dass der Abfrageplan für die Abfrage, die für die Back-End-Datenbank ausgeführt wird, so effizient wie möglich ist.  
  
##  <a name="bkmk_Design"></a>Erstellen von Modellen für die Verwendung mit dem directquery-Modus  
 Tabellarische Modelle werden anhand des Modell-Designers [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt. Der Modell-Designer erstellt alle Modelle im Arbeitsspeicher, d. h., wenn sich beim Erstellen von Modellen herausstellt, dass die Datenmenge die Kapazität des Arbeitsspeichers übersteigt, sollte nur eine Teilmenge der Daten in den von der Arbeitsbereichsdatenbank verwendeten Cache importiert werden.  
  
 Wenn Sie in den DirectQuery-Modus wechseln möchten, können Sie einfach eine Eigenschaft ändern, die den DirectQuery-Modus aktiviert. Weitere Informationen finden Sie unter [enable directquery Design Mode &#40;SSAS tabellarische&#41;](enable-directquery-mode-in-ssdt.md).  
  
 Wenn Sie diese Schritte ausführen, konfiguriert der Modell-Designer die Arbeitsbereichsdatenbank automatisch so, dass sie in einem Hybridmodus ausgeführt wird, in dem weiterhin mit den zwischengespeicherten Daten gearbeitet werden kann. Der Modell-Designer benachrichtigt Sie auch über Funktionen im Modell, die mit dem DirectQuery-Modus nicht kompatibel sind. Die folgende Liste fasst die Hauptanforderungen zusammen, die zu berücksichtigen sind:  
  
-   **Datenquellen:** Directquery-Modelle können nur Daten aus einer einzelnen SQL Server Datenquelle verwenden. Wenn der DirectQuery-Modus für ein Modell aktiviert wurde, können Sie im Modell-Designer keine anderen Datentypen verwenden, einschließlich durch Kopie-/Einfügevorgänge hinzugefügter Tabellen. Alle anderen Importoptionen werden deaktiviert. Alle in einer Abfrage enthaltenen Tabellen müssen Teil der gleichen SQL Server-Datenquelle sein. Weitere Informationen finden Sie unter [Datenquellen für directquery-Modelle](directquery-mode-ssas-tabular.md#bkmk_DataSources).  
  
-   **Unterstützung für berechnete Spalten:** Berechnete Spalten werden für directquery-Modelle nicht unterstützt. Sie können jedoch Measures und KPIs erstellen, die für Datensätze verwendet werden können. Weitere Informationen finden Sie im Abschnitt zur [Validierung](#bkmk_Validation) .  
  
-   **Eingeschränkte Verwendung von DAX-Funktionen:** Einige DAX-Funktionen können im directquery-Modus nicht verwendet werden. Daher müssen Sie Sie durch andere Funktionen ersetzen oder die Werte mit abgeleiteten Spalten in der Datenquelle erstellen. Der Modell-Designer bietet Entwurfszeitvalidierung für alle Fehler, die auftreten, wenn Sie Formeln erstellen, die nicht mit dem DirectQuery-Modus kompatibel sind. Weitere Informationen finden Sie in den folgenden Abschnitten: [Validierung](#bkmk_Validation).  
  
-   **Formel Kompatibilität:** In bestimmten bekannten Fällen kann dieselbe Formel in einem zwischengespeicherten oder hybriden Modell andere Ergebnisse zurückgeben als ein directquery-Modell, das nur den relationalen Datenspeicher verwendet. Diese Unterschiede sind eine Folge der semantischen Unterschiede zwischen der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) und SQL Server. Weitere Informationen zu diesen Unterschieden finden Sie in diesem Abschnitt: [Formel Kompatibilität](#bkmk_FormulaCompat).  
  
-   **Sicherheit:** Sie können verschiedene Methoden verwenden, um Modelle abhängig von Ihrer Bereitstellung zu sichern. Zwischengespeicherte Daten für tabellarische Modelle werden mit dem Sicherheitsmodell der Analysis Services-Instanz gesichert. DirectQuery-Modelle können mit Rollen gesichert werden, aber Sie können auch im relationalen Datenspeicher definierte Sicherheit verwenden. Das Modell kann so konfiguriert werden, dass Benutzer, die einen auf einem "Nur DirectQuery"-Modell basierenden Bericht öffnen, nur die Daten sehen können, die zu ihnen im Rahmen ihrer Berechtigungen in SQL Server zugewiesen wurden. Weitere Informationen finden Sie in diesem Abschnitt: [Sicherheit](#bkmk_Security).  
  
-   **Client Einschränkungen:** Wenn sich ein Modell im directquery-Modus befindet, kann es nur mit DAX abgefragt werden. Mit MDX können keine Abfragen erstellt werden. Dies bedeutet, dass Sie den Pivot Client in Excel nicht verwenden können, da Excel MDX verwendet.  
  
     Sie können jedoch Abfragen für ein directquery-Modell in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] erstellen, wenn Sie eine DAX-Tabellen Abfrage als Teil einer XMLA Execute-Anweisung verwenden. Weitere Informationen finden Sie unter [DAX-Abfrage Syntax Referenz] (/DAX/DAX-Syntax-Reference
  
 Wenn Sie alle Entwurfsprobleme behoben und das Modell getestet haben, kann die Bereitstellung beginnen. Nun können Sie die bevorzugte Methode zur Beantwortung von Abfragen des Modells festlegen. Möchten Sie, dass Benutzer Zugriff auf den Cache erhalten oder immer nur die relationale Datenquelle verwenden?  
  
 Wenn Sie das Modell in einem *Hybrid Modus*bereitstellen, ist der Cache weiterhin verfügbar und kann für Abfragen verwendet werden. Ein Hybridmodus bietet Ihnen zahlreiche Optionen:  
  
-   Wenn sowohl der Cache als auch die relationale Datenquelle verfügbar sind, können Sie die bevorzugte Verbindungsmethode festlegen, doch letztlich wird die zu verwendende Quelle vom Client bestimmt. Dafür wird die DirectQueryMode-Eigenschaft der Verbindungszeichenfolge verwendet.  
  
-   Sie können auch Partitionen im Cache so konfigurieren, dass die primäre Partition, die für den DirectQuery-Modus verwendet wird, niemals verarbeitet wird und immer auf die relationale Quelle verweisen muss. Es gibt viele Möglichkeiten, mithilfe von Partitionen den Modellentwurf und die Berichtsfunktionen zu optimieren. Weitere Informationen finden Sie unter [Partitionen und directquery-Modus &#40;tabellarischen SSAS-&#41;](define-partitions-in-directquery-models-ssas-tabular.md).  
  
-   Nach der Bereitstellung des Modells können Sie die bevorzugte Verbindungsmethode ändern. Sie können zum Beispiel einen Hybridmodus für Tests verwenden und den Modus **Nur DirectQuery** für das Modell erst nach gründlichen Tests von Berichten oder Abfragen, für die das Modell verwendet wird, festlegen. Weitere Informationen finden Sie unter [Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).  
  
###  <a name="bkmk_DataSources"></a>Datenquellen für directquery-Modelle  
 Sobald Sie die Entwurfsumgebung ändern, um den DirectQuery-Modus zu aktivieren, werden die Datenquellen für die Arbeitsbereichsdatenbank validiert, um sicherzustellen, dass sie aus einer einzelnen SQL Server-Datenquelle stammen. Daten aus anderen Quellen, einschließlich kopierter und eingefügter Daten, sind in DirectQuery-Modellen nicht zulässig.  
  
 Wenn Sie beabsichtigen, das Modell im DirectQuery-Modus zu verwenden, müssen Sie sicherstellen, dass alle Daten, die Sie zur Berichterstellung benötigen, in der angegebenen SQL Server-Datenbank gespeichert werden. Wenn die Daten, die Sie für Modellierung benötigen, in dieser Quelle nicht verfügbar sind, ziehen Sie die Verwendung von Integration Services oder anderen Data Warehousing-Tools in Betracht, um die Daten in eine SQL Server-Datenbank zu importieren, die als DirectQuery-Datenquelle dient.  
  
###  <a name="bkmk_Validation"></a>Validierungs-und Entwurfs Einschränkungen für den directquery-Modus  
 Wenn Sie ein Modell für die Verwendung im DirectQuery-Modus erstellen, müssen Sie zunächst einen Teil der Daten in den Cache laden. Wenn die Daten, die Sie letztendlich verwenden, zu groß für den Arbeitsspeicher sind, können Sie die Option **Vorschau & Filter** im Tabellen Import-Assistenten verwenden, um eine Teilmenge der Daten auszuwählen, oder ein SQL-Skript schreiben, um die gewünschten Daten zu erhalten.  
  
> [!WARNING]  
>  Da der DirectQuery-Modus nicht die Verwendung von berechneten Spalten unterstützt, sollten Sie, sofern Spalten vorhanden sind, die Sie kombinieren oder anderweitig bearbeiten möchten, Vorkehrungen treffen und die Spaltendefinition als Teil der Datenimportabfrage oder des Skripts erstellen.  
  
 Um Validierungsfehler anzuzeigen und zu beheben, öffnen Sie die **Fehlerliste** in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Kritische Fehler, die die Verwendung des directquery-Modus verhindern, werden auf der Registerkarte " **Fehler** " angezeigt. Sie müssen diese Fehler beheben, bevor Sie in den directquery-Modus wechseln. Die Validierungsfehler, die schwieriger zu beseitigen sind, beziehen sich in der Regel auf Formeln, die im DirectQuery-Modus nicht unterstützt werden. Eine Übersicht über Fehler im Zusammenhang mit Formeln und berechneten Spalten finden Sie im Abschnitt [Formel Kompatibilität](#bkmk_FormulaCompat).  
  
 Die folgende Liste beschreibt weitere Aspekte, die beim Erstellen eines Modells für DirectQuery-Zugriff zu berücksichtigen sind:  
  
-   Im Modus *Nur DirectQuery* können sich die Ergebnisse in einem Bericht abhängig vom Sicherheitskontext des Benutzers, der die Ergebnisse anzeigt, unterscheiden. Testen Sie Modelle mit unterschiedlichen Anmeldeinformationen, um sicherzustellen, dass Benutzer die erwarteten Ergebnisse erhalten.  
  
-   Wenn Sie ein Modell für die Ausführung im Hybridmodus konfigurieren, was entweder die Verwendung des Caches oder der Daten von SQL Server ermöglicht, beachten Sie, dass Clients, die eine Verbindung mit den einzelnen Quellen herstellen, möglicherweise andere Ergebnisse angezeigt werden. Dies hängt vom in der Verbindungszeichenfolge angegebenen Modus ab. Wenn Sie sicherstellen müssen, dass den Berichtbenutzern nur Daten von SQL Server angezeigt werden, müssen Sie den Cache löschen oder für das Modell den Modus "DirectQueryOnly" festlegen.  
  
###  <a name="bkmk_FormulaCompat"></a>Formel Kompatibilität für directquery-Modelle  
 Einige Modelle können Formeln enthalten, die im DirectQuery-Modus nicht unterstützt werden, und das Modell muss neu konzipiert werden, um Validierungsfehler zu verhindern. Für Formeln, die im DirectQuery Modus unterstützt werden, gelten die folgenden Einschränkungen:  
  
-   Berechnete Spalten werden in keinem Tabellenmodell unterstützt, für das der DirectQuery-Modus aktiviert ist, auch nicht in Hybridmodellen. Wenn Sie berechnete Spalten für ein Modell benötigen, konvertieren Sie sie mithilfe von Transact-SQL in der Importdefinition ggf. in abgeleitete Spalten.  
  
-   DirectQuery-Modelle unterstützen die Verwendung von DAX-Formeln zur Verwendung in Measures, die in satzbasierte Vorgänge für den relationalen Datenspeicher konvertiert werden. Alle Measures, die mit impliziten Measures erstellt werden, werden unterstützt.  
  
-   Nicht alle Funktionen werden unterstützt. Da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle DAX-Formeln und Measuredefinitionen in SQL-Anweisungen konvertiert, wenn sie ein DirectQuery-Modell abfragen, verursacht jede Formel, die Elemente enthält, die nicht in Transact-SQL konvertiert werden können, Validierungsfehler für das Modell. Zum Beispiel werden Zeitintelligenzfunktionen nicht unterstützt. Auch Funktionen, die unterstützt werden, zeigen möglicherweise ein anderes Verhalten, z. B. statistische Funktionen. Eine umfassende Liste der Kompatibilitätsprobleme finden Sie unter [Formel Kompatibilität im directquery-Modus](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md).  
  
-   Von einigen Formeln im Modell wird möglicherweise eine Validierung ausgeführt, wenn das Modell auf den DirectQuery-Modus umgestellt wird. Dabei werden jedoch andere Ergebnisse zurückgegeben werden, wenn die Ausführung unter Verwendung des Caches und nicht mit dem relationalen Datenspeicher. Dies liegt daran, dass bei Berechnungen für den Cache die Semantik der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) verwendet wird, das zahlreiche Funktionen zum Emulieren des Verhalten von Excel enthält, wohingegen bei Abfragen für Daten, die im relationalen Datenspeicher gespeichert sind, verbindlich die Semantik von SQL Server verwendet werden muss. Eine Liste der DAX-Funktionen, die möglicherweise andere Ergebnisse zurückgeben, wenn das Modell in Echtzeit bereitgestellt wird, finden Sie unter [Formel Kompatibilität im directquery-Modus](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md).  
  
###  <a name="bkmk_Connecting"></a>Herstellen einer Verbindung mit directquery-Modellen  
 Clients, die MDX als Abfragesprache verwenden, können keine Verbindung mit Modellen herstellen, die den DirectQuery-Modus verwenden. Wenn Sie zum Beispiel versuchen, eine MDX-Abfrage anhand eines DirectQuery-Modells zu erstellen, erhalten Sie einen Fehler wegen eines nicht gefundenen Cubes oder fehlgeschlagener Verarbeitung. Abfragen für DirectQuery-Modelle können Sie mithilfe von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], DAX-Formeln oder XMLA-Abfragen erstellen. Weitere Informationen zum Ausführen von Ad-hoc-Abfragen für tabellarische Modelle finden Sie unter [Tabellen Modell-Datenzugriff](tabular-model-data-access.md).  
  
 Wenn Sie ein Hybridmodell verwenden, können Sie angeben, ob die Benutzer eine Verbindung mit dem Cache herstellen oder DirectQuery-Daten verwenden, indem sie die Eigenschaft der Verbindungszeichenfolge "DirectQueryMode" angeben.  
  
###  <a name="bkmk_Security"></a>Sicherheit im directquery-Modus  
 Während des Modellerstellungsprozesses geben Sie die Berechtigungen für das Abrufen der Quelldaten an. Dies sind oft Ihre eigenen Anmeldeinformationen, oder ein zur Entwicklung verwendetes Konto. Wenn Sie das Modell jedoch auf den DirectQuery-Modus umstellen, ist der Sicherheitskontext komplexer:  
  
-   Berücksichtigen Sie, ob Benutzer die notwendigen Zugriffsrechte für die Daten im relationalen Datenspeicher besitzen.  
  
-   Benutzer, die das gleiche Modell oder den gleichen Bericht anzeigen, sehen abhängig vom Sicherheitskontext des Benutzers möglicherweise unterschiedliche Daten.  
  
-   Wenn der Modellcache beibehalten wurde, wird der Cache anhand des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Sicherheitsmodells (Rollen) gesichert. Der Cache kann Daten enthalten, die der Modell-Designer, jedoch nicht der Benutzer anzeigen darf. Modell- und Berichts-Designer sollten entweder den Cache löschen oder die Daten durch Steuern des Zugriffs über Rollen sichern.  
  
-   Beim Herstellen einer Verbindung mit der Datenquelle kann ein Modell, das Abfragen vom Cache beantwortet, nicht die Identität des aktuellen Benutzers annehmen. Wenn Sie beim Herstellen einer Verbindung mit der Datenquelle die Identität des aktuellen Benutzers annehmen möchten, müssen Sie den DirectQuery-Modus verwenden.  
  
-   Wenn das Berichtsmodell Sicherheit erfordert, haben Sie zwei Optionen: Sie können entweder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Rollen verwenden, oder Sie können für die Datenquelle Berechtigungen auf Zeilenebene festlegen. Sicherheit in der relationalen Datenquelle dient zur Steuerung des Zugriffs auf Tabellen. Sicherheit auf Spaltenebene wird nicht unterstützt. Wenn Benutzer in einem Bereich nicht über die Berechtigung zum Anzeigen von Umsatzzahlen aus anderen Bereichen verfügen, werden in einem Bericht, der ein auf der Umsatztabelle basierendes Measure enthält, daher Leerzeichen oder ein Fehler zurückgegeben.  
  
 Die Eigenschaft für Identitätswechseleinstellungen gibt die Anmeldeinformationen an, die verwendet werden, wenn Sie eine Verbindung mit einem Modell mit DirectQuery herstellen, und zwar entweder für ein "Nur DirectQuery"-Modell oder für ein Hybridmodell, das Abfragen mit DirectQuery beantwortet. Die Eigenschaft verfügt über die folgenden Werte:  
  
 **Vorgegebene**  
 Verwendet die im Import-Assistenten angegebenen Anmeldeinformationen, um eine Verbindung mit der Datenquelle herzustellen. Dies kann ein bestimmter Windows-Benutzer oder das Dienstkonto sein.  
  
 `ImpersonateCurrentUser`  
 Verwendet die Anmeldeinformationen des aktuellen Benutzers für die Verbindung mit der Datenquelle.  
  
 Informationen zum Festlegen dieser Eigenschaften finden Sie unter [directquery-Bereitstellungs Szenarien &#40;tabellarischen SSAS-&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
##  <a name="bkmk_PropertyList"></a>Directquery-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften aufgelistet, die Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] und in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] festlegen können, um DirectQuery zu aktivieren und die Quelle der Daten zu steuern, die für Abfragen des Modells verwendet werden.  
  
|Eigenschaftenname|BESCHREIBUNG|  
|-------------------|-----------------|  
|**DirectQueryMode-Eigenschaft**|Diese Eigenschaft ermöglicht die Verwendung des DirectQuery-Modus im Modell-Designer. Sie müssen diese Eigenschaft auf `On` festlegen, um eine der anderen DirectQuery-Eigenschaften zu ändern.<br /><br /> Weitere Informationen finden Sie unter [enable directquery Design Mode &#40;SSAS tabellarische&#41;](enable-directquery-mode-in-ssdt.md).|  
|**QueryMode-Eigenschaft**|Diese Eigenschaft gibt die Standardabfragemethode für ein DirectQuery-Modell an. Diese Eigenschaft wird im Modell-Designer festgelegt, wenn das Modell bereitgestellt wird. Eine spätere Überschreibung ist jedoch möglich. Die Eigenschaft verfügt über die folgenden Werte:<br /><br /> **Directquery** : Diese Einstellung gibt an, dass bei allen Abfragen des Modells nur die relationale Datenquelle verwendet werden soll.<br /><br /> **Directquery mit in-Memory** -diese Einstellung gibt an, dass Abfragen standardmäßig mit der relationalen Quelle beantwortet werden sollten, sofern in der Verbindungs Zeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> **In-Memory** : Diese Einstellung gibt an, dass Abfragen nur mithilfe des Caches beantwortet werden sollten.<br /><br /> **In-Memory mit directquery** : Diese Einstellung gibt standardmäßig an. für Abfragen der Cache verwendet wird, sofern in der Verbindungszeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).|  
|**DirectQueryMode-Eigenschaft**|Nachdem das Modell bereitgestellt wurde, können Sie die bevorzugte Abfragedatenquelle für ein DirectQuery-Modell durch Ändern dieser Eigenschaft in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ändern.<br /><br /> Ebenso wie die vorherige Eigenschaft gibt diese Eigenschaft die Standarddatenquelle für das Modell an. Sie besitzt die folgenden Werte:<br /><br /> **InMemory**: Abfragen können nur den Cache verwenden.<br /><br /> **Directquerywithinmemory**: bei Abfragen wird standardmäßig die relationale Datenquelle verwendet, sofern in der Verbindungs Zeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> **Inmemorywithdirectquery**: bei Abfragen wird standardmäßig der Cache verwendet, sofern in der Verbindungs Zeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> (**Directquery**: bei Abfragen wird nur die relationale Datenquelle verwendet.)<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).|  
|**Eigenschaft "Identitätswechseleinstellungen"**|Mit dieser Eigenschaft werden die Anmeldeinformationen definiert, die zum Herstellen einer Verbindung mit der SQL Server-Datenquelle zur Abfragezeit verwendet werden. Sie können diese Eigenschaft im Modell-Designer festlegen und den Wert später nach der Bereitstellung des Modells ändern.<br /><br /> Diese Anmeldeinformationen werden nur zum Beantworten von Abfragen des relationalen Datenspeichers verwendet. Sie sind nicht mit den Anmeldeinformationen für die Verarbeitung des Caches eines Hybridmodells identisch.<br /><br /> Identitätswechsel kann nicht verwendet werden, wenn das Modell nur innerhalb des Arbeitsspeichers verwendet wird. Die Einstellung `ImpersonateCurrentUser` ist ungültig, sofern das Modell nicht den DirectQuery-Modus verwendet.|  
  
 Wenn das Modell Partitionen enthält, müssen Sie zudem eine Partition auswählen, die im DirectQuery-Modus als Quelle für Abfragen verwendet werden soll. Weitere Informationen finden Sie unter [Partitionen und directquery-Modus &#40;tabellarischen SSAS-&#41;](define-partitions-in-directquery-models-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a>Verwandte Themen und Aufgaben  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Partitionen und directquery-Modus &#40;tabellarischen SSAS-&#41;](define-partitions-in-directquery-models-ssas-tabular.md)|Beschreibt, wie Partitionen in Modellen verwendet werden, die für den DirectQuery-Modus konfiguriert wurden.|  
|[DAX-Formel Kompatibilität im directquery-Modus](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|Beschreibt Einschränkungen und Kompatibilitätsanforderungen für die Formeln, die Sie in Modellen verwenden können, die für den DirectQuery-Modus konfiguriert wurden.|  
|[Aktivieren des directquery-Entwurfs Modus &#40;tabellarischen SSAS-&#41;](enable-directquery-mode-in-ssdt.md)|Beschreibt, wie Sie die Entwurfszeitumgebung ändern können, damit die Verwendung des DirectQuery-Modus unterstützt wird.|  
|[Ändern der directquery-Partition &#40;tabellarischen SSAS-&#41;](../change-the-directquery-partition-ssas-tabular.md)|Beschreibt, wie die DirectQuery-Partition geändert wird.|  
|[Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md)|Beschreibt, wie die Verbindungsmethode für Modelle, die für DirectQuery konfiguriert wurden, festgelegt oder geändert wird.|  
|[Directquery-Bereitstellungs Szenarien &#40;tabellarischen SSAS-&#41;](../directquery-deployment-scenarios-ssas-tabular.md)|Beschreibt DirectQuery-Bereitstellungsszenarien.|  
|[Konfigurieren von speicherinternem oder DirectQuery-Zugriff für eine tabellarische Modelldatenbank](enable-directquery-mode-in-ssms.md)|Grundlegendes zu DirectQuery-Konfigurationen|  
|[Löschen des Zwischenspeichers von Analysis Services](../instances/clear-the-analysis-services-caches.md)|Löschen des Caches des Tabellenmodells|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Partitionen &#40;tabellarischen SSAS-&#41;](partitions-ssas-tabular.md)   
 [Tabellarische Modellprojekte &#40;tabellarischen SSAS-&#41;](tabular-model-projects-ssas-tabular.md)   
 [In Excel analysieren &#40;tabellarischen SSAS-&#41;](analyze-in-excel-ssas-tabular.md)  
