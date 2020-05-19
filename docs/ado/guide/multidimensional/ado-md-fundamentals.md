---
title: ADO MD Grundlagen | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e19b1e816a75e3e4ccbaef62c4a583e036cda9f9
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748123"
---
# <a name="ado-md-fundamentals"></a>Grundlegendes zu ADO MD
Microsoft® ActiveX® Data Objects (Multidimensional) (ADO MD) bieten einfachen Zugriff auf mehrdimensionale Daten aus Sprachen wie Microsoft Visual Basic® Microsoft Visual C++®. ADO MD erweitert Microsoft ActiveX® Data Objects (ADO) um Objekte, die für mehrdimensionale Daten, z. b. die [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) -und [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) -Objekte, spezifisch sind. Mit ADO MD Sie das mehrdimensionale Schema durchsuchen, einen Cube Abfragen und die Ergebnisse abrufen können.  
  
 Wie ADO verwendet ADO MD einen zugrunde liegenden OLE DB-Anbieter, um Zugriff auf Daten zu erhalten. Um mit ADO MD arbeiten zu können, muss der Anbieter ein mehrdimensionaler Datenanbieter (MDP) sein, wie in der OLE DB für OLAP-Spezifikation definiert. Ein MDP stellt Daten in mehrdimensionalen Sichten anstelle von Tabellen Sichten dar, d. h., wie ein tabellarischer Datenanbieter (TDP) Daten darstellt. Weitere Informationen zur spezifischen Syntax und dem von Ihrem Anbieter unterstützten Verhalten finden Sie in der Dokumentation für Ihren OLAP-OLE DB-Anbieter.  
  
 In diesem Dokument wird davon ausgegangen, dass Sie über die Visual Basic Programmiersprache und allgemeine Kenntnisse von ADO und OLAP verfügen. Weitere Informationen finden Sie im [ADO-Programmier Handbuch](../../../ado/guide/ado-programmer-s-guide.md) und [OLE DB für die analytische Online Verarbeitung (Online Analytical Processing, OLAP)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Übersicht über mehrdimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO MD-Objektmodell](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO-Programmiererhandbuch](../../../ado/guide/ado-programmer-s-guide.md)   
 [ADO Extensions for Data Definition Language and Security (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [Übersicht über mehrdimensionale Schemas und Daten](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmieren mit ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Verwenden von ADO mit ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Arbeiten mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
