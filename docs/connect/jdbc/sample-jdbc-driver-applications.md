---
title: Beispiele für JDBC-Treiberanwendungen
description: Die Beispielanwendungen für JDBC-Treiber für SQL Server veranschaulichen verschiedene Features und bewährte Programmierverfahren, die Sie bei der Verwendung des JDBC-Treibers befolgen können.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e55eb9d0e710ba41089dcb014e9e626343ea4e91
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634263"
---
# <a name="sample-jdbc-driver-applications"></a>Beispiele für JDBC-Treiberanwendungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Die Beispielanwendungen für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] veranschaulichen verschiedene Funktionen des JDBC-Treibers. Sie zeigen darüber hinaus bewährte Programmierverfahren, die Sie nutzen können, wenn Sie den JDBC-Treiber mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank verwenden.  
  
Alle Beispielanwendungen sind in JAVA-Codedateien enthalten, die auf dem lokalen Computer kompiliert und ausgeführt werden können. Sie befinden sich in den verschiedenen Unterordnern des folgenden Pfads:  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

Die Themen in diesem Abschnitt beschreiben, wie Sie die Beispielanwendungen konfigurieren und ausführen. Darüber hinaus wird Aufgabe und Funktion der Beispielanwendungen erläutert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                                                        | BESCHREIBUNG                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Verbinden und Abrufen von Daten](connecting-and-retrieving-data.md)                       | Diese Beispielanwendungen zeigen, wie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank hergestellt wird. Sie veranschaulichen darüber hinaus verschiedene Möglichkeiten, um Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank abzurufen. |
| [Working with Data Types &#40;JDBC&#41; (Arbeiten mit Datentypen &#40;JDBC&#41;)](working-with-data-types-jdbc.md)                 | Diese Beispielanwendungen veranschaulichen die Verwendung der Datentypmethoden des JDBC-Treibers, um Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu verarbeiten.                                                                                           |
| [Arbeiten mit Resultsets](../../connect/jdbc/working-with-result-sets.md)                                   | Diese Beispielanwendungen zeigen die Verwendung von Resultsets, um Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu verarbeiten.                                                                                                         |
| [Arbeiten mit umfangreichen Daten](../../connect/jdbc/working-with-large-data.md)                                     | Diese Beispielanwendungen veranschaulichen die Verwendung der adaptiven Pufferung zum Abrufen von Daten mit einer großen Menge an Werten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank ohne den durch Servercursor verursachten Overhead.                                                      |
| [SQL-Datenermittlung und -klassifizierung](../../connect/jdbc/data-discovery-classification-sample.md) | Diese Beispielanwendung veranschaulicht das Abrufen von Informationen zur Datenermittlung und -klassifizierung in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank über ein ResultSet-Objekt mithilfe des JDBC-Treibers.                                      |
  
## <a name="see-also"></a>Weitere Informationen

[Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
