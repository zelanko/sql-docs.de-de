---
title: Informationen zu OLE DB-Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, properties
- SQL Server Native Client OLE DB provider, properties
- properties [OLE DB]
- property values [SQL Server Native Client]
ms.assetid: 0b36a61e-b542-400d-a3d2-e6f643caf2c6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 81a928d788c3461a6f24baa46906d5af40a4e7ba
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432639"
---
# <a name="about-ole-db-properties"></a>Informationen zu OLE DB-Eigenschaften
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Consumer legen Eigenschaftswerte fest, um ein bestimmtes Objektverhalten anzufordern. Zum Beispiel verwenden Consumer Eigenschaften, um die Schnittstellen anzugeben, die von einem Rowset verfügbar gemacht werden sollen. Consumer rufen die Eigenschaftswerte ab, um die Fähigkeiten eines Objekts zu ermitteln, beispielsweise eines Rowsets, einer Sitzung oder eines Datenquellenobjekts.  
  
 Jede Eigenschaft verfügt über einen Wert, einen Typ, eine Beschreibung, ein Lese-/Schreibattribut. Rowset-Eigenschaften besitzen überdies einen Indikator, der angibt, ob die Eigenschaft auf einzelne Spalten des Rowsets angewendet werden kann.  
  
 Eine Eigenschaft wird durch eine GUID und eine ganze Zahl, welche die Eigenschaften-ID darstellt, identifiziert. Ein Eigenschaftensatz ist ein Satz aller Eigenschaften, die über die gleiche GUID verfügen. Zusätzlich zu den vordefinierten OLE DB-Eigenschaft legt fest, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert die anbieterspezifische Eigenschaftensätze und Eigenschaften in diesen. Jede Eigenschaft gehört zu einer oder mehreren Eigenschaftengruppen. Eine Eigenschaftengruppe ist die Gruppe aller Eigenschaften, die für ein bestimmtes Objekt gelten. Beispiele für Eigenschaftengruppen sind die Initialisierungseigenschaftengruppe, die Datenquellen-Eigenschaftengruppe, die Sitzungseigenschaftengruppe, die Rowseteigenschaftengruppe, die Tabelleneigenschaftengruppe und die Spalteneigenschaftengruppe. Jede dieser Eigenschaftengruppen enthält Eigenschaften.  
  
 Das Festlegen von Eigenschaftswerten beinhaltet Folgendes:  
  
1.  Bestimmen der Eigenschaften, deren Werte festgelegt werden sollen  
  
2.  Bestimmen der Eigenschaftensätze, die die identifizierten Eigenschaften enthalten  
  
3.  Zuordnen eines Arrays von DBPROPSET-Strukturen, wobei für jeden identifizierten Eigenschaftensatz eine Struktur angegeben werden muss  
  
4.  Zuordnen eines Arrays von DBPROP-Strukturen, wobei für jeden Eigenschaftensatz eine Struktur angegeben werden muss. Die Anzahl der Elemente in jedem Array entspricht der Anzahl der Eigenschaften (die in Schritt 1 identifiziert wurden), die zu diesem Eigenschaftensatz gehören.  
  
5.  Füllen der DBPROP-Struktur für jede Eigenschaft  
  
6.  Eintragen der Daten (Eigenschaftensatz-GUID, Zähler für die Anzahl der Elemente und ein Zeiger auf das zugehörige DBPROP-Array) in die DBPROPSET-Struktur für jeden Eigenschaftensatz  
  
7.  Aufrufen einer Methode, um Eigenschaften festzulegen und die Anzahl und das Array von DBPROPSET-Strukturen zu übergeben  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer SQL Server Native Client OLE DB-Anbieteranwendung](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)   
 [Eigenschaften (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=112207)  
  
  
