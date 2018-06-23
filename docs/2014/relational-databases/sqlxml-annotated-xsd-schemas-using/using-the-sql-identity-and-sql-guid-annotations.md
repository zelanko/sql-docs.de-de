---
title: Mithilfe der Anmerkungen Sql:identity und Sql:guid | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b54109b005956241b87efe89a33bf1c949b792e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160872"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'
  Sie können angeben, die `sql:identity` und `sql:guid` Anmerkungen in ein XSD-Schema auf einem beliebigen Knoten, der in einer Datenbankspalte zugeordnet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Während das Updategram-Format das `updg:at-identity`-Attribut und das `updg:guid`-Attribut unterstützt, ist das beim DiffGram-Format nicht der Fall. Das `updg:at-identity`-Attribut definiert das Verhalten beim Aktualisieren der Spalte vom Typ IDENTITY. Mit dem `updg:guid`-Attribut können Sie einen GUID-Wert von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abfragen und ihn im Updategram verwenden. Weitere Informationen und Verwendungsbeispiele finden Sie unter [Einfügen von Daten mithilfe von XML-Updategrams &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Die `sql:identity`-Anmerkung und `sql:guid`-Anmerkung erweitern diese Funktionalität auf DiffGrams.  
  
 Wenn Sie ein DiffGram ausführen, wird es zunächst in ein Updategram konvertiert, dann wird das Updategram ausgeführt. Indem Sie die `sql:identity`-Anmerkung und die `sql:guid`-Anmerkung im XSD-Schema angeben, definieren Sie das Verhalten eines Updategrams. Daher werden alle Anmerkungen im Kontext eines Updategrams beschrieben. Die Anmerkungen können sowohl für DiffGrams als auch für Updategrams verwendet werden. Updategrams stellen jedoch ein leistungsfähigeres Verfahren zur Verarbeitung von Identitäts- und GUID-Werten dar.  
  
 Die `sql:identity`-Anmerkung und die `sql:guid`-Anmerkung können für ein komplexes Inhaltselement definiert werden.  
  
## <a name="sqlidentity-annotation"></a>'sql:identity'-Anmerkung  
 Sie können die `sql:identity`-Anmerkung im XSD-Schema für jeden beliebigen Knoten angeben, der einer Datenbankspalte vom Typ IDENTITY zugeordnet ist. Der für diese Anmerkung angegebene Wert definiert, wie die Spalte vom Typ IDENTITY aktualisiert wird (entweder durch Verwendung des im Updategram angegebenen Werts für die Änderung der Spalte oder durch Ignorieren des Werts, was dazu führt, dass ein von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierter Wert für diese Spalte verwendet wird).  
  
 Der `sql:identity`-Anmerkung können zwei Werte zugewiesen werden:  
  
 ignore  
 Weist das Updategram an, einen für diese Spalte im Updategram vorhandenen Wert zu ignorieren und es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu überlassen, den Identitätswert zu generieren.  
  
 useValue  
 Weist das Updategram an, den im Updategram angegebenen Wert zur Aktualisierung der Spalte vom Typ IDENTITY zu verwenden. Ein Updategram prüft nicht, ob es sich bei der Spalte um eine Identitätsspalte handelt.  
  
 Wenn das Updategram einen Wert für die Spalte vom Typ IDENTITY angibt, muss `sql:identity="useValue"` im Schema angegeben sein.  
  
## <a name="sqlguid-annotation"></a>'sql:guid'-Anmerkung  
 Ein Updategram kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veranlassen, einen GUID-Wert zu generieren, der dann im Updategram verwendet wird. Im Kontext von DiffGrams können Sie mit der `sql:guid`-Anmerkung angeben, ob ein von SQL Server generierter GUID-Wert oder der im Updategram angegebene Wert für die betreffende Spalte verwendet werden soll.  
  
 Der `sql:guid`-Anmerkung können zwei Werte zugewiesen werden:  
  
 generate  
 Gibt an, dass der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierte GUID-Wert im Updatevorgang für diese Spalte verwendet werden soll.  
  
 useValue  
 Gibt an, dass der im Updategram angegebene Wert für die Spalte verwendet werden soll. Dies ist der Standardwert.  
  
  