---
title: Beispiele für JDBC-Treiberanwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4021211b212ace43257637dad348a0da1e82f21
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "76910734"
---
# <a name="sample-jdbc-driver-applications"></a>Beispiele für JDBC-Treiberanwendungen

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Die Beispielanwendungen für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulichen verschiedene Funktionen des JDBC-Treibers. Sie zeigen darüber hinaus bewährte Programmierverfahren, die Sie nutzen können, wenn Sie den JDBC-Treiber mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank verwenden.  
  
Alle Beispielanwendungen sind in JAVA-Codedateien enthalten, die auf dem lokalen Computer kompiliert und ausgeführt werden können. Sie befinden sich in den verschiedenen Unterordnern des folgenden Pfads:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

 Die Themen in diesem Abschnitt beschreiben, wie Sie die Beispielanwendungen konfigurieren und ausführen. Darüber hinaus wird Aufgabe und Funktion der Beispielanwendungen erläutert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                                                                  | BESCHREIBUNG                                                                                                                                                                                                                                                                   |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Verbinden und Abrufen von Daten](../../../connect/jdbc/code-samples/connecting-and-retrieving-data.md)                              | Diese Beispielanwendungen zeigen, wie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank hergestellt wird. Sie veranschaulichen darüber hinaus verschiedene Möglichkeiten, um Daten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abzurufen. |
| [Working with Data Types &#40;JDBC&#41; (Arbeiten mit Datentypen &#40;JDBC&#41;)](../../../connect/jdbc/code-samples/working-with-data-types-jdbc.md)                        | Diese Beispielanwendungen veranschaulichen die Verwendung der Datentypmethoden des JDBC-Treibers, um Daten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank zu verarbeiten.                                                                                              |
| [Arbeiten mit Resultsets](../../../connect/jdbc/code-samples/working-with-result-sets.md)                                          | Diese Beispielanwendungen zeigen die Verwendung von Resultsets, um Daten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank zu verarbeiten.                                                                                                            |
| [Arbeiten mit umfangreichen Daten](../../../connect/jdbc/code-samples/working-with-large-data.md)                                            | Diese Beispielanwendungen veranschaulichen die Verwendung der adaptiven Pufferung zum Abrufen von Daten mit einer großen Menge an Werten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank ohne den durch Servercursor verursachten Overhead.                                                         |
| [SQL-Datenermittlung und -klassifizierung](../../jdbc/code-samples/data-discovery-and-classification-sample.md) | Diese Beispielanwendung veranschaulicht das Abrufen von Informationen zur Datenermittlung und -klassifizierung in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank über ein ResultSet-Objekt mithilfe des JDBC-Treibers.                                            |
  
## <a name="see-also"></a>Weitere Informationen

[Übersicht über den JDBC-Treiber](../../../connect/jdbc/overview-of-the-jdbc-driver.md)
