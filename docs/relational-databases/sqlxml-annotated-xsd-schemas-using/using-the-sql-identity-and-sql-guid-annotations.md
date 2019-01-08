---
title: "Verwenden der Anmerkungen: Identity ' und Sql:guid | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 611e202007fb9a5b9438e3432984c3722e264bd7
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52522864"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können angeben, die **: Identity '** und **Sql:guid** Anmerkungen in ein XSD-Schema auf einem beliebigen Knoten, der einer Datenbankspalte in zugeordnet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Während das Updategram-Format unterstützt die **Updg: auf Identität** und **updg: GUID** Attribute, das DiffGram-Format nicht. Die **Updg: auf Identität** -Attribut definiert das Verhalten beim Aktualisieren einer Spalte vom Typ IDENTITY. Die **updg: GUID** Attribut können Sie zum Abrufen eines GUID-Wert von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und in das Updategram verwenden. Weitere Informationen und Verwendungsbeispiele finden Sie unter [Einfügen von Daten mithilfe von XML-Updategrams &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
 Die **: Identity '** und **Sql:guid** -Anmerkung erweitern diese Funktionalität auf DiffGrams.  
  
 Wenn Sie ein DiffGram ausführen, wird es zunächst in ein Updategram konvertiert, dann wird das Updategram ausgeführt. Durch Angabe der **: Identity '** und **Sql:guid** Anmerkungen im XSD-Schema, das Sie definieren das Verhalten eines Updategrams sind. Daher werden alle Anmerkungen im Kontext eines Updategrams beschrieben. Die Anmerkungen können sowohl für DiffGrams als auch für Updategrams verwendet werden. Updategrams stellen jedoch ein leistungsfähigeres Verfahren zur Verarbeitung von Identitäts- und GUID-Werten dar.  
  
 Die **: Identity '** und **Sql:guid** Anmerkungen können für ein komplexes Inhaltselement definiert werden.  
  
## <a name="sqlidentity-annotation"></a>'sql:identity'-Anmerkung  
 Sie können angeben, die **: Identity '** -Anmerkung im XSD-Schema auf einem beliebigen Knoten, der einer Datenbankspalte vom Typ IDENTITY zugeordnet ist. Für diese Anmerkung angegebene Wert definiert, wie die Spalte vom Typ IDENTITY aktualisiert wird (entweder mithilfe des im Updategram angegebenen Werts zum Ändern der Spalte oder durch ignorieren des Werts, in diesem Fall eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generierter Wert für diese Spalte verwendet wird).  
  
 Die **: Identity '** -Anmerkung kann zwei Werte zugewiesen werden:  
  
 ignore  
 Weist das Updategram an, einen für diese Spalte im Updategram vorhandenen Wert zu ignorieren und es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu überlassen, den Identitätswert zu generieren.  
  
 useValue  
 Weist das Updategram an, den im Updategram angegebenen Wert zur Aktualisierung der Spalte vom Typ IDENTITY zu verwenden. Ein Updategram prüft nicht, ob es sich bei der Spalte um eine Identitätsspalte handelt.  
  
 Wenn das Updategram einen Wert für die Spalte vom Typ IDENTITY angibt. die **: Identity ' = "UseValue"** im Schema angegeben werden.  
  
## <a name="sqlguid-annotation"></a>'sql:guid'-Anmerkung  
 Ein Updategram kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veranlassen, einen GUID-Wert zu generieren, der dann im Updategram verwendet wird. Im Kontext von DiffGrams können Sie die **Sql:guid** Anmerkung, die angeben, ob einen GUID-Wert verwendet, die von SQL Server generiert wird, oder verwenden Sie den Wert, der im Updategram für diese Spalte bereitgestellt wird.  
  
 Die **Sql:guid** -Anmerkung kann zwei Werte zugewiesen werden:  
  
 generate  
 Gibt an, dass der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierte GUID-Wert im Updatevorgang für diese Spalte verwendet werden soll.  
  
 useValue  
 Gibt an, dass der im Updategram angegebene Wert für die Spalte verwendet werden soll. Dies ist der Standardwert.  
  
  
