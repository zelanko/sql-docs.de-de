---
title: Grundlegendes zu ADO MD | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bbff704e174dd824eca7b1f71c8f9d3fc15def51
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704413"
---
# <a name="ado-md-fundamentals"></a>Grundlegendes zu ADO MD
Microsoft® ActiveX® Data Objects (Multidimensional) (ADO MD) bietet einfachen Zugriff auf mehrdimensionale Daten in Sprachen wie z. B. Microsoft Visual Basic®, fest Microsoft Visual C++®. ADO MD erweitert Microsoft ActiveX® Data Objects (ADO), um die Objekte, die speziell für mehrdimensionale Daten, z. B. enthalten die [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) und [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) Objekte. Mit ADO MD können Sie mehrdimensionales Schema durchsuchen, Abfragen ein Cubes und die Ergebnisse abzurufen.  
  
 ADO MD verwendet wie ADO zugrunde liegenden OLE DB-Anbieter für den Zugriff auf Daten. Zum Arbeiten mit ADO MD muss der Anbieter einen Anbieter für mehrdimensionale Daten (MDP) sein, wie in der OLE DB für OLAP-Spezifikation definiert. Ein MDP zeigt Daten in multidimensionalen Ansichten anstelle von tabellarischen Ansichten ist wie ein tabellarischer Datenanbieter (TDP) Daten dargestellt. Lesen Sie die Dokumentation für den OLAP-OLE DB-Anbieter für Weitere Informationen zur spezifischen Syntax und Verhalten, die von Ihrem Anbieter unterstützt.  
  
 In diesem Dokument wird davon ausgegangen, die Programmiersprache Visual Basic-Kenntnisse und eine allgemeine Kenntnisse von ADO und OLAP. Weitere Informationen finden Sie unter den [ADO Programmer's Guide](../../../ado/guide/ado-programmer-s-guide.md) und [OLE DB für Online Analytical Processing (OLAP)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Übersicht über multidimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO Programmer's Guide](../../../ado/guide/ado-programmer-s-guide.md)   
 [ADO-Erweiterungen für Datendefinitionssprache und Sicherheit (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Übersicht über multidimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
