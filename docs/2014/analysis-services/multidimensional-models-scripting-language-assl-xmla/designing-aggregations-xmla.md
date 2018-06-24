---
title: Entwerfen von Aggregationen (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statistical information [XML for Analysis]
- batches [XML for Analysis]
- aggregations [Analysis Services], XML for Analysis
- XMLA, aggregations
- queries [XMLA]
- XML for Analysis, aggregations
- iterative aggregation process [XMLA]
ms.assetid: 4dd27afa-10c7-408d-bc24-ca74217ddbcb
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e2e2d5be45ba679cfa0c0ea39928e5b43d30c3a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048635"
---
# <a name="designing-aggregations-xmla"></a>Entwerfen von Aggregationen (XMLA)
  Aggregationsentwürfe werden den Partitionen einer bestimmten Measuregruppe zugeordnet, um sicherzustellen, dass die Partitionen beim Speichern von Aggregationen die gleiche Struktur verwenden. Verwenden einheitliche Speicherstruktur für Partitionen können Sie ganz einfach Partitionen definieren, die später zusammengeführt werden können mithilfe der [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) Befehl. Weitere Informationen zu Aggregationsentwürfen finden Sie unter [Aggregationen und Aggregationsentwürfe](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Um Aggregationen für einen Aggregationsentwurf definieren möchten, können Sie die [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) -Befehl in XML for Analysis (XMLA). Der `DesignAggregations`-Befehl umfasst Eigenschaften, die angeben, welche Aggregationsentwürfe als Referenz verwendet sollen und wie der Entwurfsprozess basierend auf dieser Referenz gesteuert werden kann. Mit dem `DesignAggregations`-Befehl und den dazugehörigen Eigenschaften können Sie Aggregationen iterativ oder in einem Batch entwerfen und anschließend die resultierenden Entwurfsstatistiken anzeigen, um den Entwurfsprozess zu bewerten.  
  
## <a name="specifying-an-aggregation-design"></a>Angeben eines Aggregationsentwurfs  
 Die [Objekt](../xmla/xml-elements-properties/object-element-xmla.md) Eigenschaft von der `DesignAggregations` -Befehls muss einen Objektverweis auf einen vorhandenen Aggregationsentwurf enthalten. Der Objektverweis enthält einen Datenbankbezeichner, Cubebezeichner, Measuregruppenbezeichner und Aggregationsentwurfsbezeichner. Wenn der Aggregationsentwurf noch nicht vorhanden ist, tritt ein Fehler auf.  
  
## <a name="controlling-the-design-process"></a>Steuern des Entwurfsprozesses  
 Sie können die folgenden Eigenschaften des `DesignAggregations`-Befehls verwenden, um den Algorithmus zu steuern, der zum Definieren von Aggregationen für den Aggregationsentwurf verwendet wird.  
  
-   Die [Schritte](../xmla/xml-elements-properties/steps-element-xmla.md) Eigenschaft bestimmt, wie viele Wiederholungen der `DesignAggregations` -Befehl abwartet, bevor er die Steuerung an die Clientanwendung zurückgibt.  
  
-   Die [Zeit](../xmla/xml-elements-properties/time-element-xmla.md) Eigenschaft bestimmt, wie viele Millisekunden die `DesignAggregations` -Befehl abwartet, bevor er die Steuerung an die Clientanwendung zurückgibt.  
  
-   Die [Optimierung](../xmla/xml-elements-properties/optimization-element-xmla.md) Eigenschaft bestimmt den geschätzten Prozentsatz der leistungsverbesserung der `DesignAggregations` Befehl zu erreichen versuchen sollte. Wenn Sie Aggregationen iterativ entwerfen, müssen Sie diese Eigenschaft nur beim ersten Befehl senden.  
  
-   Die [Speicher](../xmla/xml-elements-properties/storage-element-xmla.md) Eigenschaft bestimmt die geschätzte Menge an Festplattenspeicher, in Bytes, der verwendet wird, indem Sie die `DesignAggregations` Befehl. Wenn Sie Aggregationen iterativ entwerfen, müssen Sie diese Eigenschaft nur beim ersten Befehl senden.  
  
-   Die [' materialisieren '](../xmla/xml-elements-properties/materialize-element-xmla.md) Eigenschaft bestimmt, ob die `DesignAggregations` Befehl sollte während des Entwurfsprozesses definierten Aggregationen zu erstellen. Wenn Sie Aggregationen iterativ entwerfen, sollte diese Eigenschaft auf den Wert FALSE gesetzt werden, bis Sie bereit sind, die entworfenen Aggregationen zu speichern. Wenn sie auf den Wert TRUE gesetzt wird, wird der aktuelle Entwurfsprozess beendet, und die definierten Aggregationen werden dem angegebenen Aggregationsentwurf hinzugefügt.  
  
## <a name="specifying-queries"></a>Angeben von Abfragen  
 Der DesignAggregations-Befehl unterstützt Verwendungsbasierte optimierungsbefehle durch die Einbindung mindestens `Query` Elemente in der [Abfragen](../xmla/xml-elements-properties/queries-element-xmla.md) Eigenschaft. Die `Queries` Eigenschaft enthalten kann, eine oder mehrere [Abfrage](../xmla/xml-elements-properties/query-element-xmla.md) Elemente. Wenn die `Queries`-Eigenschaft keine `Query`-Elemente enthält, verwendet der im `Object`-Element angegebene Aggregationsentwurf eine Standardstruktur, die einen allgemeinen Satz Aggregationen enthält. Dieser allgemeine Aggregationssatz wurde so entworfen, dass er die in der `Optimization`- und der `Storage`-Eigenschaft des `DesignAggregations`-Befehls angegebenen Kriterien erfüllt.  
  
 Jede `Query` Element stellt eine Zielabfrage aus, die der Entwurfsprozess nutzt, um Aggregationen zu definieren, die am häufigsten verwendeten Abfragen abzielen. Sie können entweder Ihre eigenen zielabfragen festlegen oder können Sie die Informationen gespeichert, die von einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] im Abfrageprotokoll einbezogen, zum Abrufen von Informationen über die am häufigsten verwendeten Abfragen. Der Assistent für verwendungsbasierte Optimierung verwendet beim Senden eines `DesignAggregations`-Befehls das Abfrageprotokoll basierend auf Zeit, Verwendung oder einem bestimmten Benutzer. Weitere Informationen finden Sie unter [Verwendungsbasierte Optimierung-Assistent F1-Hilfe](../usage-based-optimization-wizard-f1-help.md).  
  
 Wenn Sie Aggregationen iterativ entwerfen, nur müssen Sie zielabfragen im ersten übergeben `DesignAggregations` Befehl, weil die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz diese zielabfragen speichert und verwendet diese Abfragen während der nachfolgenden `DesignAggregations` Befehle. Nachdem Sie Zielabfragen im ersten `DesignAggregations`-Befehl eines iterativen Prozesses weitergegeben haben, generiert jeder darauf folgende `DesignAggregations`-Befehl, der über Zielabfragen in der `Queries`-Eigenschaft verfügt, einen Fehler.  
  
 Das `Query`-Element enthält einen durch Trennzeichen getrennten Wert, der die folgenden Argumente beinhaltet:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Häufigkeit*  
 Ein Gewichtungsfaktor, der der Anzahl der Male entspricht, die eine Abfrage zuvor ausgeführt wurde. Wenn die `Query` Element eine neue Abfrage darstellt, die *Häufigkeit* Wert stellt den Gewichtungsfaktor an, von der Entwurfsprozess für die Evaluierung der Abfrage verwendet. Bei steigendem Häufigkeitswert, steigt die Gewichtung auf die Abfrage während des Entwurfsprozesses.  
  
 *DataSet*  
 Eine numerische Zeichenfolge, die festlegt, welche Attribute einer Dimension in die Abfrage eingebunden werden. Diese Zeichenfolge muss die gleiche Anzahl an Zeichen wie die Anzahl an Attributen in der Dimension haben. null (0) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension nicht in der Abfrage enthalten ist. Eins (1) zeigt an, dass das Attribut an der angegebenen Ordnungsposition für die angegebene Dimension in der Abfrage enthalten ist.  
  
 Beispielsweise bezieht sich die Zeichenfolge "011" auf eine Abfrage mit einer Dimension mit drei Attributen, von denen das zweite und dritte Attribut in der Abfrage enthalten sind.  
  
> [!NOTE]  
>  Einige Attribute sind von der Berücksichtigung im Dataset ausgenommen. Weitere Informationen über ausgenommene Attribute finden Sie unter [Abfrageelement &#40;XMLA&#41;](../xmla/xml-elements-properties/query-element-xmla.md).  
  
 Jede Dimension in der Measuregruppe, die den Aggregationsentwurf enthält wird dargestellt, indem eine *Dataset* Wert in der `Query` Element. Die Reihenfolge der *Dataset* -Werte muss der Reihenfolge der Dimensionen entsprechen, die in die Measuregruppe eingebunden sind.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Entwerfen von Aggregationen mithilfe von iterativen oder Batchprozessen  
 Sie können den `DesignAggregations`-Befehl als Teil eines iterativen oder eines Batchprozesses verwenden, je nach der für den Entwurfsprozess erforderlichen Interaktivität.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Entwerfen von Aggregationen mithilfe eines iterativen Prozesses  
 Wenn Sie Aggregationen iterativ entwerfen möchten, senden Sie mehrere `DesignAggregations`-Befehle, um eine Feinsteuerung des Entwurfsprozesses zu ermöglichen. Der Aggregationsentwurfs-Assistent verwendet ebenfalls diesen Ansatz, um eine Feinsteuerung des Entwurfsprozesses zu ermöglichen. Weitere Informationen finden Sie unter [Aggregation Design-Assistent F1-Hilfe](../aggregation-design-wizard-f1-help.md).  
  
> [!NOTE]  
>  Eine explizite Sitzung ist erforderlich, damit Aggregationen iterativ entworfen werden können. Weitere Informationen zu expliziten Sitzungen finden Sie unter [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md).  
  
 Um den iterativen Prozess zu starten, senden Sie zunächst einen `DesignAggregations`-Befehl, der die folgenden Informationen enthält:  
  
-   Der `Storage`- und der `Optimization`-Eigenschaftenwert, auf den der gesamte Entwurfsprozess abzielt.  
  
-   Der `Steps`- und der `Time`-Eigenschaftenwert, auf den der erste Schritt des Entwurfsprozesses begrenzt ist.  
  
-   Wenn Sie die verwendungsbasierte Optimierung verwenden möchten, die `Queries`-Eigenschaft, die die Zielabfragen enthält, auf die der gesamte Entwurfsprozess abzielt.  
  
-   Die auf den Wert FALSE gesetzte `Materialize`-Eigenschaft. Das Festlegen dieser Eigenschaft auf FALSE gibt an, dass der Entwurfsprozess die definierten Aggregationen nicht im Aggregationsentwurf speichert, wenn der Befehl abgeschlossen ist.  
  
 Wenn der erste `DesignAggregations`-Befehl beendet wird, gibt der Befehl ein Rowset zurück, das Entwurfsstatistiken enthält. Sie können diese Entwurfsstatistiken bewerten, um zu bestimmen, ob der Entwurfsprozess fortgeführt werden sollte oder abgeschlossen ist. Wenn der Prozess fortgeführt werden soll, senden Sie einen weiteren `DesignAggregations`-Befehl, der den `Steps`- und den `Time`-Wert enthält, mit dem dieser Schritt des Entwurfsprozesses begrenzt wird. Sie können diese Entwurfsstatistiken bewerten und anschließend bestimmen, ob der Entwurfsprozess fortgeführt werden sollte. Dieser iterative Prozess des Sendens von `DesignAggregations`-Befehlen und Auswertens der Ergebnisse wird so lange fortgeführt, bis Sie Ihre Ziele erreicht und einen passenden Satz Aggregationen definiert haben.  
  
 Nachdem Sie den gewünschten Satz Aggregationen erreicht haben, senden Sie einen abschließenden `DesignAggregations`-Befehl. Bei diesem abschließenden `DesignAggregations`-Befehl sollte die `Steps`-Eigenschaft auf 1 und die `Materialize`-Eigenschaft auf TRUE festgelegt sein. Mit diesen Einstellungen schließt der abschließende `DesignAggregations`-Befehl den Entwurfsprozess ab und speichert die definierten Aggregationen im Aggregationsentwurf.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Entwerfen von Aggregationen mithilfe eines Batchprozesses  
 Sie können Aggregationen auch in einem Batchprozess entwerfen, indem Sie einen einzelnen `DesignAggregations`-Befehl senden, der die Eigenschaftswerte `Steps`, `Time`, `Storage` und `Optimization` enthält, auf die der gesamte Entwurfsprozess abzielt und auf die er begrenzt ist. Wenn Sie die verwendungsbasierte Optimierung verwenden möchten, sollten die Zielabfragen, auf die der Entwurfsprozess abzielt, ebenfalls in der `Queries`-Eigenschaft enthalten sein. Stellen Sie außerdem sicher, dass die `Materialize`-Eigenschaft auf den Wert TRUE festgelegt ist, damit der Entwurfsprozess die definierten Aggregationen im Aggregationsentwurf speichert, wenn der Befehl abgeschlossen ist.  
  
 Sie können Aggregationen mithilfe eines Batchprozesses entweder in einer impliziten oder in einer expliziten Sitzung entwerfen. Weitere Informationen zu impliziten und expliziten Sitzungen finden Sie unter [Verwalten von Verbindungen und Sitzungen &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Zurückgeben von Entwurfsstatistiken  
 Wenn der `DesignAggregations`-Befehl die Steuerung über die Clientanwendung zurückgibt, gibt er auch ein Rowset zurück, das eine einzelne Zeile enthält, die die Entwurfsstatistiken für den Befehl darstellt. Das Rowset enthält die in der folgenden Tabelle aufgeführten Spalten.  
  
|Spalte|Datentyp|Description|  
|------------|---------------|-----------------|  
|Schritte|Integer|Die Anzahl der Schritte, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung abgewartet werden.|  
|Uhrzeit|Lange ganze Zahl|Die Anzahl der Millisekunden, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung abgewartet werden.|  
|Optimization|Double|Der geschätzte Prozentwert der Leistungsverbesserung, der durch den Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung erreicht wird.|  
|Speicherung|Lange ganze Zahl|Die geschätzte Anzahl an Bytes, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung abgewartet werden.|  
|Aggregations|Lange ganze Zahl|Die Anzahl der Aggregationen, die vom Befehl vor dem Zurückgeben der Steuerung an die Clientanwendung definiert werden.|  
|LastStep|Boolean|Gibt an, ob die Daten im Rowset den letzten Schritt im Entwurfsprozess darstellen. Wenn die `Materialize`-Eigenschaft des Befehls auf den Wert TRUE festgelegt wurde, wird der Wert dieser Spalte ebenfalls auf TRUE festgelegt.|  
  
 Sie können die Entwurfsstatistiken verwenden, die im Rowset enthalten sind, das nach jedem `DesignAggregations`-Befehl sowohl im iterativen als auch im Batchentwurf zurückgegeben wird. Im iterativen Entwurf können Sie die Entwurfsstatistiken verwenden, um den Status zu bestimmen und anzuzeigen. Wenn Sie Aggregationen in einem Batch entwerfen, können Sie die Entwurfsstatistiken verwenden, um die Anzahl der vom Befehl erstellten Aggregationen zu bestimmen.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  