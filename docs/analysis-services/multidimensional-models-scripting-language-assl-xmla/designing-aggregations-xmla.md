---
title: Entwerfen von Aggregationen (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9f681b3c99bd0e8351a844f28b16be6249de199
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147185"
---
# <a name="designing-aggregations-xmla"></a>Entwerfen von Aggregationen (XMLA)
  Aggregationsentwürfe werden den Partitionen einer bestimmten Measuregruppe zugeordnet, um sicherzustellen, dass die Partitionen beim Speichern von Aggregationen die gleiche Struktur verwenden. Dieselbe Speicherstruktur für Partitionen mit können Sie ganz einfach Partitionen definieren, die später zusammengeführt werden können mithilfe der [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) Befehl. Weitere Informationen zu Aggregationsentwürfen finden Sie unter [Aggregationen und Aggregationsentwürfe](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Um Aggregationen für einen Aggregationsentwurf definieren möchten, können Sie die [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) -Befehl in XML for Analysis (XMLA) verwenden. Die **DesignAggregations** Befehl verfügt über Eigenschaften, die identifizieren, welche aggregationsentwürfe als einen Verweis und zur Steuerung des Entwurfsprozess basierend auf diesen Verweis zu verwenden. Mithilfe der **DesignAggregations** Befehl und seine Eigenschaften, können Sie Aggregationen iterativ oder in einem Batch entwerfen und zeigen Sie dann die resultierenden entwurfsstatistiken, um den Entwurfsprozess zu bewerten.  
  
## <a name="specifying-an-aggregation-design"></a>Angeben eines Aggregationsentwurfs  
 Die [Objekt](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) Eigenschaft der **DesignAggregations** -Befehls muss einen Objektverweis auf einen vorhandenen Aggregationsentwurf enthalten. Der Objektverweis enthält einen Datenbankbezeichner, Cubebezeichner, Measuregruppenbezeichner und Aggregationsentwurfsbezeichner. Wenn der Aggregationsentwurf noch nicht vorhanden ist, tritt ein Fehler auf.  
  
## <a name="controlling-the-design-process"></a>Steuern des Entwurfsprozesses  
 Können Sie die folgenden Eigenschaften der **DesignAggregations** Befehl aus, um den Algorithmus für das Definieren von Aggregationen für den Aggregationsentwurf zu steuern:  
  
-   Die [Schritte](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/steps-element-xmla) Eigenschaft bestimmt, wie viele Iterationen der **DesignAggregations** -Befehl abwartet, bevor er die Steuerung an die Clientanwendung zurückgibt.  
  
-   Die [Zeit](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/time-element-xmla) Eigenschaft bestimmt, wie viele Millisekunden die **DesignAggregations** -Befehl abwartet, bevor er die Steuerung an die Clientanwendung zurückgibt.  
  
-   Die [Optimierung](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/optimization-element-xmla) Eigenschaft bestimmt den geschätzten Prozentsatz der Verbesserung der Leistung der **DesignAggregations** Befehl zu erreichen versuchen sollte. Wenn Sie Aggregationen iterativ entwerfen, müssen Sie diese Eigenschaft nur beim ersten Befehl senden.  
  
-   Die [Storage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/storage-element-xmla) Eigenschaft bestimmt die geschätzte Menge an Festplattenspeicher, in Bytes ein, die die **DesignAggregations** Befehl. Wenn Sie Aggregationen iterativ entwerfen, müssen Sie diese Eigenschaft nur beim ersten Befehl senden.  
  
-   Die [materialisieren](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/materialize-element-xmla) Eigenschaft bestimmt, ob die **DesignAggregations** Befehl während des Entwurfsprozesses definierten Aggregationen erstellen soll. Wenn Sie Aggregationen iterativ entwerfen, sollte diese Eigenschaft auf den Wert FALSE gesetzt werden, bis Sie bereit sind, die entworfenen Aggregationen zu speichern. Wenn sie auf den Wert TRUE gesetzt wird, wird der aktuelle Entwurfsprozess beendet, und die definierten Aggregationen werden dem angegebenen Aggregationsentwurf hinzugefügt.  
  
## <a name="specifying-queries"></a>Angeben von Abfragen  
 Der DesignAggregations-Befehl unterstützt Verwendungsbasierte optimierungsbefehle durch die Einbindung ein oder mehrerer **Abfrage** Elemente in der [Abfragen](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/queries-element-xmla) Eigenschaft. Die **Abfragen** Eigenschaft enthalten kann, eine oder mehrere [Abfrage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla) Elemente. Wenn die **Abfragen** Eigenschaft enthält keine **Abfrage** Elemente, der Aggregationsentwurf angegeben, der **Objekt** Element verwendet eine Standardstruktur, enthält ein allgemeinen Satz Aggregationen. Diese allgemeinen Satz Aggregationen wurde entwickelt, um die angegebenen Kriterien erfüllen die **Optimierung** und **Storage** Eigenschaften der **DesignAggregations** Befehl.  
  
 Jedes **Query** -Element stellt eine Zielabfrage dar, die der Entwurfsprozess nutzt, um Aggregationen zu definieren, die auf die am häufigsten verwendeten Abfragen abzielen. Sie können entweder Ihre eigenen Zielabfragen festlegen oder die Informationen nutzen, die von einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im Abfrageprotokoll gespeichert werden, um Informationen über die am häufigsten verwendeten Abfragen abzurufen. Den Assistenten für Verwendungsbasierte Optimierung verwendet Abfrageprotokoll einbezogen, um basierend auf der Zeit, Verwendung oder einen angegebenen Benutzer beim Senden einer **DesignAggregations** Befehl. Weitere Informationen finden Sie unter [Verwendungsbasierte Optimierung-Assistent F1-Hilfe](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763).  
  
 Wenn Sie Aggregationen iterativ entwerfen, müssen Sie Zielabfragen nur im ersten **DesignAggregations** -Befehl weitergeben, da die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz diese Zielabfragen speichert und diese während folgender **DesignAggregations** -Befehle erneut verwendet. Nachdem Sie Zielabfragen im ersten **DesignAggregations** -Befehl eines iterativen Prozesses weitergegeben haben, generiert jeder darauf folgende **DesignAggregations** -Befehl, der über Zielabfragen in der **Queries** -Eigenschaft verfügt, einen Fehler.  
  
 Das **Query** -Element enthält einen durch Trennzeichen getrennten Wert, der die folgenden Argumente beinhaltet:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Häufigkeit*  
 Ein Gewichtungsfaktor, der der Anzahl der Male entspricht, die eine Abfrage zuvor ausgeführt wurde. Wenn das **Query** -Element eine neue Abfrage darstellt, gibt der *Frequency* -Wert den Gewichtungsfaktor an, der vom Entwurfsprozess für die Evaluierung der Abfrage verwendet wird. Bei steigendem Häufigkeitswert, steigt die Gewichtung auf die Abfrage während des Entwurfsprozesses.  
  
 *Dataset*  
 Eine numerische Zeichenfolge, die festlegt, welche Attribute einer Dimension in die Abfrage eingebunden werden. Diese Zeichenfolge muss die gleiche Anzahl an Zeichen wie die Anzahl an Attributen in der Dimension haben. null (0) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension nicht in der Abfrage enthalten ist. Eins (1) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension in der Abfrage enthalten ist.  
  
 Beispielsweise bezieht sich die Zeichenfolge "011" auf eine Abfrage mit einer Dimension mit drei Attributen, von denen das zweite und dritte Attribut in der Abfrage enthalten sind.  
  
> [!NOTE]  
>  Einige Attribute sind von der Berücksichtigung im Dataset ausgenommen. Weitere Informationen über ausgenommene Attribute finden Sie unter [Abfrageelement &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla).  
  
 Jede Dimension in der Measuregruppe, die einen Aggregationsentwurf enthält, wird durch einen *Dataset* -Wert im **Query** -Element dargestellt. Die Reihenfolge der *Dataset* -Werte muss der Reihenfolge der Dimensionen entsprechen, die in die Measuregruppe eingebunden sind.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Entwerfen von Aggregationen mithilfe von iterativen oder Batchprozessen  
 Sie können die **DesignAggregations** Befehl als Teil eines iterativen oder einen Batchprozess, abhängig von der durch den Entwurfsprozess erforderlichen Interaktivität.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Entwerfen von Aggregationen mithilfe eines iterativen Prozesses  
 Wenn Sie Aggregationen iterativ entwerfen möchten, senden Sie mehrere **DesignAggregations** Befehle aus, um eine feinsteuerung des Entwurfsprozesses ermöglichen. Der Aggregationsentwurfs-Assistent verwendet ebenfalls diesen Ansatz, um eine Feinsteuerung des Entwurfsprozesses zu ermöglichen. Weitere Informationen finden Sie unter [Aggregation Design-Assistent F1-Hilfe](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d).  
  
> [!NOTE]  
>  Eine explizite Sitzung ist erforderlich, damit Aggregationen iterativ entworfen werden können. Weitere Informationen zu expliziten Sitzungen finden Sie unter [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
 Um den iterativen Prozess zu starten, senden Sie zunächst eine **DesignAggregations** -Befehl, der die folgenden Informationen enthält:  
  
-   Die **Storage** und **Optimierung** Standardwerte für die Eigenschaft auf dem der gesamte Entwurfsprozess abzielt.  
  
-   Die **Schritte** und **Zeit** Eigenschaftswerte, die auf dem der erste Schritt des Entwurfsprozesses begrenzt ist.  
  
-   Wenn Sie Verwendungsbasierte Optimierung verwenden möchten, die **Abfragen** -Eigenschaft, die das Ziel enthält abfragt, auf dem der gesamte Entwurfsprozess abzielt.  
  
-   Die **materialisieren** -Eigenschaft auf "false" festgelegt. Das Festlegen dieser Eigenschaft auf FALSE gibt an, dass der Entwurfsprozess die definierten Aggregationen nicht im Aggregationsentwurf speichert, wenn der Befehl abgeschlossen ist.  
  
 Wenn die erste **DesignAggregations** Befehl beendet ist ist, der Befehl gibt ein Rowset, das entwurfsstatistiken enthält. Sie können diese Entwurfsstatistiken bewerten, um zu bestimmen, ob der Entwurfsprozess fortgeführt werden sollte oder abgeschlossen ist. Wenn der Vorgang fortgesetzt werden soll, Sie senden eine andere **DesignAggregations** Befehl, der die **Schritte** und **Zeit** Werte, die mit dem Verarbeiten von diesem Schritt des Entwurfs ist begrenzt. Sie können diese Entwurfsstatistiken bewerten und anschließend bestimmen, ob der Entwurfsprozess fortgeführt werden sollte. Dieser iterative Prozess des Sendens von **DesignAggregations** -Befehlen und auswertens der Ergebnisse wird fortgesetzt, bis Sie Ihre Ziele erreicht und einen passenden Satz Aggregationen definiert haben.  
  
 Nachdem Sie die Menge der Aggregationen, die Sie möchten erreicht haben, senden Sie einen abschließenden **DesignAggregations** Befehl. Diesem abschließenden **DesignAggregations** Befehl müsste die **Schritte** -Eigenschaft auf 1 festgelegt und die zugehörige **materialisieren** Eigenschaft auf "true" festgelegt ist. Mithilfe dieser Einstellungen, die abschließende **DesignAggregations** Befehl schließt den Entwurfsprozess ab und speichert die definierten Aggregationen im Aggregationsentwurf.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Entwerfen von Aggregationen mithilfe eines Batchprozesses  
 Sie können auch die Aggregationen in einem Batchprozess entwerfen, durch Senden einer einzelnes **DesignAggregations** Befehl, der die **Schritte**, **Zeit**, **Speicher** , und **Optimierung** Eigenschaftswerte auf dem der gesamte Entwurfsprozess abzielt und beschränkt. Wenn Sie Verwendungsbasierte Optimierung verwenden möchten, die zielabfragen, auf dem der Entwurfsprozess abzielt ist, auch in eingeschlossen werden soll die **Abfragen** Eigenschaft. Stellen Sie außerdem sicher, dass die **materialisieren** -Eigenschaftensatz auf "true" werden, damit der Entwurfsprozess die definierten Aggregationen im Aggregationsentwurf speichert, wenn der Befehl abgeschlossen ist.  
  
 Sie können Aggregationen mithilfe eines Batchprozesses entweder in einer impliziten oder in einer expliziten Sitzung entwerfen. Weitere Informationen zu impliziten und expliziten Sitzungen finden Sie unter [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Zurückgeben von Entwurfsstatistiken  
 Wenn die **DesignAggregations** Befehl übergibt die Steuerung an die Clientanwendung, die der Befehl gibt ein Rowset, eine einzelne Zeile enthält, die die entwurfsstatistiken für den Befehl darstellt. Das Rowset enthält die in der folgenden Tabelle aufgeführten Spalten.  
  
|Spalte|Datentyp|Description|  
|------------|---------------|-----------------|  
|Schritte|Integer|Die Anzahl der Schritte, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung abgewartet werden.|  
|Uhrzeit|Lange ganze Zahl|Die Anzahl der Millisekunden, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung abgewartet werden.|  
|Optimization|Double|Der geschätzte Prozentwert der Leistungsverbesserung, der durch den Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung erreicht wird.|  
|Speicherung|Lange ganze Zahl|Die geschätzte Anzahl an Bytes, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung abgewartet werden.|  
|Aggregations|Lange ganze Zahl|Die Anzahl der Aggregationen, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung definiert werden.|  
|LastStep|Boolean|Gibt an, ob die Daten im Rowset den letzten Schritt im Entwurfsprozess darstellen. Wenn die **materialisieren** Eigenschaft des Befehls wurde festgelegt auf "true", der Wert dieser Spalte wird festgelegt auf "true".|  
  
 Sie können die entwurfsstatistiken verwenden, die im nach jedem zurückgegebenen Rowset enthalten sind **DesignAggregations** Befehl sowohl iterative auch im batchentwurf. Im iterativen Entwurf können Sie die Entwurfsstatistiken verwenden, um den Status zu bestimmen und anzuzeigen. Wenn Sie Aggregationen in einem Batch entwerfen, können Sie die Entwurfsstatistiken verwenden, um die Anzahl der vom Befehl erstellten Aggregationen zu bestimmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
