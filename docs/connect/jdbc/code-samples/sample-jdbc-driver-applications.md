---
title: Beispielanwendungen für JDBC-Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c62942580b403bbacd62c6fc65e0a19b0960f1e6
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39457814"
---
# <a name="sample-jdbc-driver-applications"></a>Beispiele für JDBC-Treiberanwendungen

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Die Beispielanwendungen für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulichen verschiedene Funktionen des JDBC-Treibers. Sie zeigen darüber hinaus bewährte Programmierverfahren, die Sie nutzen können, wenn Sie den JDBC-Treiber mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank verwenden.  
  
Alle Beispielanwendungen sind in JAVA-Codedateien enthalten, die auf dem lokalen Computer kompiliert und ausgeführt werden können. Sie befinden sich in den verschiedenen Unterordnern des folgenden Pfads:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

 Die Themen in diesem Abschnitt beschreiben, wie Sie die Beispielanwendungen konfigurieren und ausführen. Darüber hinaus wird Aufgabe und Funktion der Beispielanwendungen erläutert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                                                                  | und Beschreibung                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Verbinden und Abrufen von Daten](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)                              | Diese Beispielanwendungen zeigen, wie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank hergestellt wird. Sie veranschaulichen darüber hinaus verschiedene Möglichkeiten, um Daten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank abzurufen. |
| [Working with Data Types &#40;JDBC&#41; (Arbeiten mit Datentypen &#40;JDBC&#41;)](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)                        | Diese Beispielanwendungen veranschaulichen die Verwendung der Datentypmethoden des JDBC-Treibers, um Daten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank zu verarbeiten.                                                                                              |
| [Arbeiten mit Resultsets](../../../connect/jdbc/code-samples/working-with-result-sets.md)                                          | Diese Beispielanwendungen zeigen die Verwendung von Resultsets, um Daten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank zu verarbeiten.                                                                                                            |
| [Arbeiten mit umfangreichen Daten](../../../connect/jdbc/code-samples/working-with-large-data.md)                                            | Diese Beispielanwendungen veranschaulichen die Verwendung der adaptiven Pufferung zum Abrufen von Daten mit einer großen Menge an Werten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Datenbank ohne den durch Servercursor verursachten Overhead.                                                         |
| [SQL-Datenermittlung und -klassifizierung](../../jdbc/code-samples/data-discovery-and-classification-sample.md) | Diese beispielanwendung veranschaulicht, wie zum Abrufen Datenermittlung und-Klassifizierung in Informationen enthaltenen eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Datenbank aus einem ResultSet-Objekt, das JDBC-Treiber verwenden.                                            |
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../../connect/jdbc/overview-of-the-jdbc-driver.md)