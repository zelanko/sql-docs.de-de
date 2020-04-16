---
title: Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'
description: Erfahren Sie, wie Sie die Anmerkungen sql:identity und sql:guid in einem XSD-Schema verwenden, um das Verhalten eines XML-Aktualisierungsgrams zu definieren.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f581c1a5c0d925d48df5a16d95cdb141e2d48f83
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388109"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können die Anmerkungen **sql:identity** und **sql:guid** in einem XSD-Schema auf [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]jedem Knoten angeben, der einer Datenbankspalte in zugeordnet ist. Während das updategram-Format die Attribute **updg:at-identity** und **updg:guid** unterstützt, ist dies im DiffGram-Format nicht der Fall. Das **updg:at-identity-Attribut** definiert das Verhalten beim Aktualisieren einer IDENTITY-Typspalte. Mit dem **updg:guid-Attribut** können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen GUID-Wert abrufen und im Updategram verwenden. Weitere Informationen und Arbeitsbeispiele finden Sie unter [Einfügen von Daten mithilfe von XML-Aktualisierungsgrammen &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Die annotations **sql:identity** und **sql:guid** erweitern diese Funktionalität auf DiffGrams.  
  
 Wenn Sie ein DiffGram ausführen, wird es zunächst in ein Updategram konvertiert, dann wird das Updategram ausgeführt. Durch Die Angabe der Annotationen **sql:identity** und **sql:guid** im XSD-Schema definieren Sie das Verhalten eines Updategramms. Daher werden alle Anmerkungen im Kontext eines Updategrams beschrieben. Die Anmerkungen können sowohl für DiffGrams als auch für Updategrams verwendet werden. Updategrams stellen jedoch ein leistungsfähigeres Verfahren zur Verarbeitung von Identitäts- und GUID-Werten dar.  
  
 Die annotationen **sql:identity** und **sql:guid** können für ein komplexes Inhaltselement definiert werden.  
  
## <a name="sqlidentity-annotation"></a>'sql:identity'-Anmerkung  
 Sie können die **sql:identity-Anmerkung** im XSD-Schema auf jedem Knoten angeben, der einer IDENTITY-Datenbankspalte zugeordnet ist. Der für diese Anmerkung angegebene Wert definiert, wie die Spalte IDENTITY-Typ aktualisiert wird (entweder durch Verwendung des im Updategramm [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angegebenen Wertes zum Ändern der Spalte oder durch Ignorieren des Werts, in diesem Fall wird ein -generierter Wert für diese Spalte verwendet).  
  
 Der **sql:identity-Anmerkung** können zwei Werte zugewiesen werden:  
  
 ignore  
 Weist das Updategram an, einen für diese Spalte im Updategram vorhandenen Wert zu ignorieren und es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu überlassen, den Identitätswert zu generieren.  
  
 useValue  
 Weist das Updategram an, den im Updategram angegebenen Wert zur Aktualisierung der Spalte vom Typ IDENTITY zu verwenden. Ein Updategram prüft nicht, ob es sich bei der Spalte um eine Identitätsspalte handelt.  
  
 Wenn das updategram einen Wert für die Spalte IDENTITY-Type angibt, muss der **sql:identity="useValue"** im Schema angegeben werden.  
  
## <a name="sqlguid-annotation"></a>'sql:guid'-Anmerkung  
 Ein Updategram kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veranlassen, einen GUID-Wert zu generieren, der dann im Updategram verwendet wird. Im Kontext von DiffGrams können Sie die **sql:guid-Anmerkung** verwenden, um anzugeben, ob ein GUID-Wert verwendet werden soll, der von SQL Server generiert wird, oder den Wert, der im Updategramm für diese Spalte bereitgestellt wird.  
  
 Der **sql:guid-Anmerkung** können zwei Werte zugewiesen werden:  
  
 generate  
 Gibt an, dass der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierte GUID-Wert im Updatevorgang für diese Spalte verwendet werden soll.  
  
 useValue  
 Gibt an, dass der im Updategram angegebene Wert für die Spalte verwendet werden soll. Dies ist der Standardwert.  
  
  
