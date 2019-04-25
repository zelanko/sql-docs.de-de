---
title: DirectQuery-Modus (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.realtime.f1
ms.assetid: 45ad2965-05ec-4fb1-a164-d8060b562ea5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9226a15351e8c6fcc938543d04fc95b0237f702b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757373"
---
# <a name="directquery-mode-ssas-tabular"></a>DirectQuery-Modus (SSAS – tabellarisch)
  Analysis Services können Sie die Daten abrufen und Erstellen von Berichten aus einem tabellarischen Modell durch das Abrufen von Daten und Aggregate direkt aus einem relationalen Datenbanksystem mithilfe *DirectQuery-Modus*. In diesem Thema werden die Unterschiede zwischen standardmäßigen Tabellenmodellen erläutert, die sich nur in Arbeitsspeicher- und Tabellenmodellen befinden, die eine relationale Datenquelle abfragen können. Zudem wird erklärt, wie Sie Modelle für die Verwendung im DirectQuery-Modus entwerfen und bereitstellen können.  
  
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
  
##  <a name="bkmk_Benefits"></a> Vorteile des DirectQuery-Modus  
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
  
##  <a name="bkmk_Design"></a> Erstellen von Modellen zur Verwendung mit DirectQuery-Modus  
 Tabellarische Modelle werden anhand des Modell-Designers [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt. Der Modell-Designer erstellt alle Modelle im Arbeitsspeicher, d. h., wenn sich beim Erstellen von Modellen herausstellt, dass die Datenmenge die Kapazität des Arbeitsspeichers übersteigt, sollte nur eine Teilmenge der Daten in den von der Arbeitsbereichsdatenbank verwendeten Cache importiert werden.  
  
 Wenn Sie in den DirectQuery-Modus wechseln möchten, können Sie einfach eine Eigenschaft ändern, die den DirectQuery-Modus aktiviert. Weitere Informationen finden Sie unter [DirectQuery-Entwurfsmodus aktivieren &#40;SSAS – tabellarisch&#41;](enable-directquery-mode-in-ssdt.md).  
  
 Wenn Sie diese Schritte ausführen, konfiguriert der Modell-Designer die Arbeitsbereichsdatenbank automatisch so, dass sie in einem Hybridmodus ausgeführt wird, in dem weiterhin mit den zwischengespeicherten Daten gearbeitet werden kann. Der Modell-Designer benachrichtigt Sie auch über Funktionen im Modell, die mit dem DirectQuery-Modus nicht kompatibel sind. Die folgende Liste fasst die Hauptanforderungen zusammen, die zu berücksichtigen sind:  
  
-   **Datenquellen:** DirectQuery-Modelle können nur Daten aus einer einzelnen SQL Server-Datenquelle verwenden. Wenn der DirectQuery-Modus für ein Modell aktiviert wurde, können Sie im Modell-Designer keine anderen Datentypen verwenden, einschließlich durch Kopie-/Einfügevorgänge hinzugefügter Tabellen. Alle anderen Importoptionen werden deaktiviert. Alle in einer Abfrage enthaltenen Tabellen müssen Teil der gleichen SQL Server-Datenquelle sein. Finden Sie unter [Datenquellen für DirectQuery-Modelle](directquery-mode-ssas-tabular.md#bkmk_DataSources)für Weitere Informationen.  
  
-   **Unterstützung für berechnete Spalten:** Berechnete Spalten werden für DirectQuery-Modelle nicht unterstützt. Sie können jedoch Measures und KPIs erstellen, die für Datensätze verwendet werden können. Finden Sie im Abschnitt [Überprüfung](#bkmk_Validation) für Weitere Informationen.  
  
-   **Eingeschränkte Verwendung von DAX-Funktionen:** Einige DAX-Funktionen können nicht im DirectQuery-Modus verwendet werden, deshalb müssen Sie sie durch andere Funktionen ersetzen oder erstellen Sie die Werte mit abgeleiteten Spalten in der Datenquelle. Der Modell-Designer bietet Entwurfszeitvalidierung für alle Fehler, die auftreten, wenn Sie Formeln erstellen, die nicht mit dem DirectQuery-Modus kompatibel sind. Finden Sie unter den folgenden Abschnitten Weitere Informationen: [Überprüfung](#bkmk_Validation).  
  
-   **Formelkompatibilität:** In bestimmten bekannten Fällen ergeben sich aus der Anwendung derselben Formel in einem zwischengespeicherten oder hybriden Modell andere Ergebnisse als in einem DirectQuery-Modell, in dem nur der relationale Datenspeicher verwendet wird. Diese Unterschiede sind eine Folge der semantischen Unterschiede zwischen der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) und SQL Server. Weitere Informationen zu diesen Unterschieden finden Sie in diesem Abschnitt: [Formelkompatibilität](#bkmk_FormulaCompat).  
  
-   **Sicherheit:** Sie können verschiedene Methoden verwenden, um je nach Bereitstellungsform der Modelle zu sichern. Zwischengespeicherte Daten für tabellarische Modelle werden mit dem Sicherheitsmodell der Analysis Services-Instanz gesichert. DirectQuery-Modelle können mit Rollen gesichert werden, aber Sie können auch im relationalen Datenspeicher definierte Sicherheit verwenden. Das Modell kann so konfiguriert werden, dass Benutzer, die einen auf einem "Nur DirectQuery"-Modell basierenden Bericht öffnen, nur die Daten sehen können, die zu ihnen im Rahmen ihrer Berechtigungen in SQL Server zugewiesen wurden. Finden Sie in diesem Abschnitt finden Sie weitere Informationen: [Sicherheit](#bkmk_Security).  
  
-   **Clienteinschränkungen:** Wenn Sie ein Modell im DirectQuery-Modus befindet, kann es nur mit DAX abgefragt werden. Mit MDX können keine Abfragen erstellt werden. Dies bedeutet, dass Sie den Pivot Client in Excel nicht verwenden können, da Excel MDX verwendet.  
  
     Sie können jedoch Abfragen für ein DirectQuery-Modell in erstellen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] bei Verwendung von einer DAX-Tabellenabfrage als Teil einer XMLA Execute-Anweisung für Weitere Informationen finden Sie unter [Syntaxreferenz für DAX-Abfrage](https://msdn.microsoft.com/library/ee634217.aspx).  
  
 Wenn Sie alle Entwurfsprobleme behoben und das Modell getestet haben, kann die Bereitstellung beginnen. Nun können Sie die bevorzugte Methode zur Beantwortung von Abfragen des Modells festlegen. Möchten Sie, dass Benutzer Zugriff auf den Cache erhalten oder immer nur die relationale Datenquelle verwenden?  
  
 Wenn es sich bei der Bereitstellung des Modells in einem *Hybridmodus*, des Caches weiterhin verfügbar und kann für Abfragen verwendet werden. Ein Hybridmodus bietet Ihnen zahlreiche Optionen:  
  
-   Wenn sowohl der Cache als auch die relationale Datenquelle verfügbar sind, können Sie die bevorzugte Verbindungsmethode festlegen, doch letztlich wird die zu verwendende Quelle vom Client bestimmt. Dafür wird die DirectQueryMode-Eigenschaft der Verbindungszeichenfolge verwendet.  
  
-   Sie können auch Partitionen im Cache so konfigurieren, dass die primäre Partition, die für den DirectQuery-Modus verwendet wird, niemals verarbeitet wird und immer auf die relationale Quelle verweisen muss. Es gibt viele Möglichkeiten, mithilfe von Partitionen den Modellentwurf und die Berichtsfunktionen zu optimieren. Weitere Informationen finden Sie unter [Partitionen und DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](define-partitions-in-directquery-models-ssas-tabular.md).  
  
-   Nach der Bereitstellung des Modells können Sie die bevorzugte Verbindungsmethode ändern. Sie können zum Beispiel einen Hybridmodus für Tests verwenden und den Modus **Nur DirectQuery** für das Modell erst nach gründlichen Tests von Berichten oder Abfragen, für die das Modell verwendet wird, festlegen. Weitere Informationen finden Sie unter [Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).  
  
###  <a name="bkmk_DataSources"></a> Datenquellen für DirectQuery-Modelle  
 Sobald Sie die Entwurfsumgebung ändern, um den DirectQuery-Modus zu aktivieren, werden die Datenquellen für die Arbeitsbereichsdatenbank validiert, um sicherzustellen, dass sie aus einer einzelnen SQL Server-Datenquelle stammen. Daten aus anderen Quellen, einschließlich kopierter und eingefügter Daten, sind in DirectQuery-Modellen nicht zulässig.  
  
 Wenn Sie beabsichtigen, das Modell im DirectQuery-Modus zu verwenden, müssen Sie sicherstellen, dass alle Daten, die Sie zur Berichterstellung benötigen, in der angegebenen SQL Server-Datenbank gespeichert werden. Wenn die Daten, die Sie für Modellierung benötigen, in dieser Quelle nicht verfügbar sind, ziehen Sie die Verwendung von Integration Services oder anderen Data Warehousing-Tools in Betracht, um die Daten in eine SQL Server-Datenbank zu importieren, die als DirectQuery-Datenquelle dient.  
  
###  <a name="bkmk_Validation"></a> Validierungs- und Entwurfsbeschränkungen für den DirectQuery-Modus  
 Wenn Sie ein Modell für die Verwendung im DirectQuery-Modus erstellen, müssen Sie zunächst einen Teil der Daten in den Cache laden. Wenn die letztlich verwendete Daten in den Arbeitsspeicher passen zu groß ist, können Sie mithilfe der **Vorschau & Filter** Option im Tabellenimport-Assistenten, um eine Teilmenge der Daten auszuwählen, oder schreiben ein SQL-Skript zum Abrufen der Daten, die Sie möchten.  
  
> [!WARNING]  
>  Da der DirectQuery-Modus nicht die Verwendung von berechneten Spalten unterstützt, sollten Sie, sofern Spalten vorhanden sind, die Sie kombinieren oder anderweitig bearbeiten möchten, Vorkehrungen treffen und die Spaltendefinition als Teil der Datenimportabfrage oder des Skripts erstellen.  
  
 Um Validierungsfehler anzuzeigen und zu beheben, öffnen Sie die **Fehlerliste** in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Schwerwiegende Fehler, die Verwendung des DirectQuery-Modus verhindern, werden auf der Registerkarte **Fehler** angezeigt. Sie müssen diese Fehler beheben, bevor Sie in den DirectQuery-Modus wechseln. Die Validierungsfehler, die schwieriger zu beseitigen sind, beziehen sich in der Regel auf Formeln, die im DirectQuery-Modus nicht unterstützt werden. Siehe den Abschnitt [Formelkompatibilität](#bkmk_FormulaCompat), eine Übersicht über Fehler im Zusammenhang mit Formeln und berechneten Spalten.  
  
 Die folgende Liste beschreibt weitere Aspekte, die beim Erstellen eines Modells für DirectQuery-Zugriff zu berücksichtigen sind:  
  
-   Im Modus *Nur DirectQuery* können sich die Ergebnisse in einem Bericht abhängig vom Sicherheitskontext des Benutzers, der die Ergebnisse anzeigt, unterscheiden. Testen Sie Modelle mit unterschiedlichen Anmeldeinformationen, um sicherzustellen, dass Benutzer die erwarteten Ergebnisse erhalten.  
  
-   Wenn Sie ein Modell für die Ausführung im Hybridmodus konfigurieren, was entweder die Verwendung des Caches oder der Daten von SQL Server ermöglicht, beachten Sie, dass Clients, die eine Verbindung mit den einzelnen Quellen herstellen, möglicherweise andere Ergebnisse angezeigt werden. Dies hängt vom in der Verbindungszeichenfolge angegebenen Modus ab. Wenn Sie sicherstellen müssen, dass den Berichtbenutzern nur Daten von SQL Server angezeigt werden, müssen Sie den Cache löschen oder für das Modell den Modus "DirectQueryOnly" festlegen.  
  
###  <a name="bkmk_FormulaCompat"></a> Formelkompatibilität für DirectQuery-Modelle  
 Einige Modelle können Formeln enthalten, die im DirectQuery-Modus nicht unterstützt werden, und das Modell muss neu konzipiert werden, um Validierungsfehler zu verhindern. Für Formeln, die im DirectQuery Modus unterstützt werden, gelten die folgenden Einschränkungen:  
  
-   Berechnete Spalten werden in keinem Tabellenmodell unterstützt, für das der DirectQuery-Modus aktiviert ist, auch nicht in Hybridmodellen. Wenn Sie berechnete Spalten für ein Modell benötigen, konvertieren Sie sie mithilfe von Transact-SQL in der Importdefinition ggf. in abgeleitete Spalten.  
  
-   DirectQuery-Modelle unterstützen die Verwendung von DAX-Formeln zur Verwendung in Measures, die in satzbasierte Vorgänge für den relationalen Datenspeicher konvertiert werden. Alle Measures, die mit impliziten Measures erstellt werden, werden unterstützt.  
  
-   Nicht alle Funktionen werden unterstützt. Da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle DAX-Formeln und Measuredefinitionen in SQL-Anweisungen konvertiert, wenn sie ein DirectQuery-Modell abfragen, verursacht jede Formel, die Elemente enthält, die nicht in Transact-SQL konvertiert werden können, Validierungsfehler für das Modell. Zum Beispiel werden Zeitintelligenzfunktionen nicht unterstützt. Auch Funktionen, die unterstützt werden, zeigen möglicherweise ein anderes Verhalten, z. B. statistische Funktionen. Eine vollständige Liste der Kompatibilitätsprobleme, finden Sie unter [Formelkompatibilität im DirectQuery-Modus](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md).  
  
-   Von einigen Formeln im Modell wird möglicherweise eine Validierung ausgeführt, wenn das Modell auf den DirectQuery-Modus umgestellt wird. Dabei werden jedoch andere Ergebnisse zurückgegeben werden, wenn die Ausführung unter Verwendung des Caches und nicht mit dem relationalen Datenspeicher. Dies liegt daran, dass bei Berechnungen für den Cache die Semantik der xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) verwendet wird, das zahlreiche Funktionen zum Emulieren des Verhalten von Excel enthält, wohingegen bei Abfragen für Daten, die im relationalen Datenspeicher gespeichert sind, verbindlich die Semantik von SQL Server verwendet werden muss. Eine Liste der DAX-Funktionen, die möglicherweise andere Ergebnisse zurückgeben, wenn das Modell bereitgestellt wird in Echtzeit, finden Sie unter [Formelkompatibilität im DirectQuery-Modus](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md).  
  
###  <a name="bkmk_Connecting"></a> Herstellen einer Verbindung mit DirectQuery-Modelle  
 Clients, die MDX als Abfragesprache verwenden, können keine Verbindung mit Modellen herstellen, die den DirectQuery-Modus verwenden. Wenn Sie zum Beispiel versuchen, eine MDX-Abfrage anhand eines DirectQuery-Modells zu erstellen, erhalten Sie einen Fehler wegen eines nicht gefundenen Cubes oder fehlgeschlagener Verarbeitung. Abfragen für DirectQuery-Modelle können Sie mithilfe von [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], DAX-Formeln oder XMLA-Abfragen erstellen. Weitere Informationen dazu, wie Sie ad-hoc-Abfragen für tabellarische Modelle ausführen können, finden Sie unter [Tabular Model Data Access](tabular-model-data-access.md).  
  
 Wenn Sie ein Hybridmodell verwenden, können Sie angeben, ob die Benutzer eine Verbindung mit dem Cache herstellen oder DirectQuery-Daten verwenden, indem sie die Eigenschaft der Verbindungszeichenfolge "DirectQueryMode" angeben.  
  
###  <a name="bkmk_Security"></a> Sicherheit im DirectQuery-Modus  
 Während des Modellerstellungsprozesses geben Sie die Berechtigungen für das Abrufen der Quelldaten an. Dies sind oft Ihre eigenen Anmeldeinformationen, oder ein zur Entwicklung verwendetes Konto. Wenn Sie das Modell jedoch auf den DirectQuery-Modus umstellen, ist der Sicherheitskontext komplexer:  
  
-   Berücksichtigen Sie, ob Benutzer die notwendigen Zugriffsrechte für die Daten im relationalen Datenspeicher besitzen.  
  
-   Benutzer, die das gleiche Modell oder den Bericht anzeigen, möglicherweise unterschiedliche Daten, abhängig vom Sicherheitskontext des Benutzers angezeigt.  
  
-   Wenn der Modellcache beibehalten wurde, wird der Cache anhand des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Sicherheitsmodells (Rollen) gesichert. Der Cache kann Daten enthalten, die der Modell-Designer, jedoch nicht der Benutzer anzeigen darf. Modell- und Berichts-Designer sollten entweder den Cache löschen oder die Daten durch Steuern des Zugriffs über Rollen sichern.  
  
-   Beim Herstellen einer Verbindung mit der Datenquelle kann ein Modell, das Abfragen vom Cache beantwortet, nicht die Identität des aktuellen Benutzers annehmen. Wenn Sie beim Herstellen einer Verbindung mit der Datenquelle die Identität des aktuellen Benutzers annehmen möchten, müssen Sie den DirectQuery-Modus verwenden.  
  
-   Wenn das Berichtsmodell Sicherheit erfordert, haben Sie zwei Optionen: Sie können entweder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Rollen verwenden, oder Sie können für die Datenquelle Berechtigungen auf Zeilenebene festlegen. Sicherheit in der relationalen Datenquelle dient zur Steuerung des Zugriffs auf Tabellen. Sicherheit auf Spaltenebene wird nicht unterstützt. Wenn Benutzer in einem Bereich nicht über die Berechtigung zum Anzeigen von Umsatzzahlen aus anderen Bereichen verfügen, werden in einem Bericht, der ein auf der Umsatztabelle basierendes Measure enthält, daher Leerzeichen oder ein Fehler zurückgegeben.  
  
 Die Eigenschaft für Identitätswechseleinstellungen gibt die Anmeldeinformationen an, die verwendet werden, wenn Sie eine Verbindung mit einem Modell mit DirectQuery herstellen, und zwar entweder für ein "Nur DirectQuery"-Modell oder für ein Hybridmodell, das Abfragen mit DirectQuery beantwortet. Die Eigenschaft verfügt über die folgenden Werte:  
  
 **Default**  
 Verwendet die im Import-Assistenten angegebenen Anmeldeinformationen, um eine Verbindung mit der Datenquelle herzustellen. Dies kann ein bestimmter Windows-Benutzer oder das Dienstkonto sein.  
  
 `ImpersonateCurrentUser`  
 Verwendet die Anmeldeinformationen des aktuellen Benutzers für die Verbindung mit der Datenquelle.  
  
 Informationen zum Festlegen dieser Eigenschaften finden Sie unter [DirectQuery-Bereitstellungsszenarien &#40;SSAS – tabellarisch&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
##  <a name="bkmk_PropertyList"></a> DirectQuery-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften aufgelistet, die Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] und in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] festlegen können, um DirectQuery zu aktivieren und die Quelle der Daten zu steuern, die für Abfragen des Modells verwendet werden.  
  
|Eigenschaftenname|Description|  
|-------------------|-----------------|  
|**DirectQueryMode property**|Diese Eigenschaft ermöglicht die Verwendung des DirectQuery-Modus im Modell-Designer. Sie müssen diese Eigenschaft auf `On` festlegen, um eine der anderen DirectQuery-Eigenschaften zu ändern.<br /><br /> Weitere Informationen finden Sie unter [DirectQuery-Entwurfsmodus aktivieren &#40;SSAS – tabellarisch&#41;](enable-directquery-mode-in-ssdt.md).|  
|**QueryMode-Eigenschaft**|Diese Eigenschaft gibt die Standardabfragemethode für ein DirectQuery-Modell an. Diese Eigenschaft wird im Modell-Designer festgelegt, wenn das Modell bereitgestellt wird. Eine spätere Überschreibung ist jedoch möglich. Die Eigenschaft verfügt über die folgenden Werte:<br /><br /> **DirectQuery** -diese Einstellung gibt an, alle Abfragen für das Modell, nur die relationale Datenquelle verwendet werden soll.<br /><br /> **DirectQuery mit InMemory** – Diese Einstellung gibt an, dass Abfragen standardmäßig mit der relationalen Quelle beantwortet werden sollten, sofern in der Verbindungszeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> **InMemory** – Diese Einstellung gibt an, dass Abfragen nur mithilfe des Caches beantwortet werden sollten.<br /><br /> **InMemory mit DirectQuery** – Diese Einstellung gibt an, dass standardmäßig für Abfragen der Cache verwendet wird, sofern in der Verbindungszeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).|  
|**DirectQueryMode property**|Nachdem das Modell bereitgestellt wurde, können Sie die bevorzugte Abfragedatenquelle für ein DirectQuery-Modell durch Ändern dieser Eigenschaft in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ändern.<br /><br /> Ebenso wie die vorherige Eigenschaft gibt diese Eigenschaft die Standarddatenquelle für das Modell an. Sie besitzt die folgenden Werte:<br /><br /> **InMemory**: Abfragen können nur den Cache verwenden.<br /><br /> **DirectQuerywithInMemory**: Bei Abfragen wird standardmäßig die relationale Datenquelle verwendet, sofern in der Verbindungszeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> **InMemorywithDirectQuery**: Für Abfragen wird standardmäßig der Cache verwendet, sofern in der Verbindungszeichenfolge vom Client nichts Gegenteiliges angegeben wurde.<br /><br /> (**DirectQuery**: Für Abfragen wird nur die relationale Datenquelle verwendet.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).|  
|**Eigenschaft "identitätswechseleinstellungen"**|Mit dieser Eigenschaft werden die Anmeldeinformationen definiert, die zum Herstellen einer Verbindung mit der SQL Server-Datenquelle zur Abfragezeit verwendet werden. Sie können diese Eigenschaft im Modell-Designer festlegen und den Wert später nach der Bereitstellung des Modells ändern.<br /><br /> Diese Anmeldeinformationen werden nur zum Beantworten von Abfragen des relationalen Datenspeichers verwendet. Sie sind nicht mit den Anmeldeinformationen für die Verarbeitung des Caches eines Hybridmodells identisch.<br /><br /> Identitätswechsel kann nicht verwendet werden, wenn das Modell nur innerhalb des Arbeitsspeichers verwendet wird. Die Einstellung `ImpersonateCurrentUser` ist ungültig, sofern das Modell nicht den DirectQuery-Modus verwendet.|  
  
 Wenn das Modell Partitionen enthält, müssen Sie zudem eine Partition auswählen, die im DirectQuery-Modus als Quelle für Abfragen verwendet werden soll. Weitere Informationen finden Sie unter [Partitionen und DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](define-partitions-in-directquery-models-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Verwandte Themen und Tasks  
  
|Thema|Description|  
|-----------|-----------------|  
|[Partitionen und DirectQuery-Modus &#40;SSAS – tabellarisch&#41;](define-partitions-in-directquery-models-ssas-tabular.md)|Beschreibt, wie Partitionen in Modellen verwendet werden, die für den DirectQuery-Modus konfiguriert wurden.|  
|[DAX-Formelkompatibilität im DirectQuery-Modus](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|Beschreibt Einschränkungen und Kompatibilitätsanforderungen für die Formeln, die Sie in Modellen verwenden können, die für den DirectQuery-Modus konfiguriert wurden.|  
|[Aktivieren des DirectQuery-Entwurfsmodus &#40;SSAS – tabellarisch&#41;](enable-directquery-mode-in-ssdt.md)|Beschreibt, wie Sie die Entwurfszeitumgebung ändern können, damit die Verwendung des DirectQuery-Modus unterstützt wird.|  
|[Ändern der DirectQuery-Partition &#40;SSAS – tabellarisch&#41;](../change-the-directquery-partition-ssas-tabular.md)|Beschreibt, wie die DirectQuery-Partition geändert wird.|  
|[Festlegen oder Ändern der bevorzugten Verbindungsmethode für DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md)|Beschreibt, wie die Verbindungsmethode für Modelle, die für DirectQuery konfiguriert wurden, festgelegt oder geändert wird.|  
|[DirectQuery-Bereitstellungsszenarien &#40;SSAS – tabellarisch&#41;](../directquery-deployment-scenarios-ssas-tabular.md)|Beschreibt DirectQuery-Bereitstellungsszenarien.|  
|[Konfigurieren von speicherinternem oder DirectQuery-Zugriff für eine tabellarische Modelldatenbank](enable-directquery-mode-in-ssms.md)|Grundlegendes zu DirectQuery-Konfigurationen|  
|[Löschen des Zwischenspeichers von Analysis Services](../instances/clear-the-analysis-services-caches.md)|Löschen des Caches des Tabellenmodells|  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;SSAS – tabellarisch&#41;](partitions-ssas-tabular.md)   
 [Tabellenmodellprojekte &#40;SSAS – tabellarisch&#41;](tabular-model-projects-ssas-tabular.md)   
 [Analysieren in Excel &#40;SSAS – tabellarisch&#41;](analyze-in-excel-ssas-tabular.md)  
