---
title: Arbeiten mit Datentypen (JDBC)
description: Hier erfahren Sie anhand der gezeigten Beispielanwendungen, wie Sie mit Datentypen im JDBC-Treiber für SQL Server arbeiten.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6994e7ce587cf72d7879c79604cbe3c68873ddf0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86923282"
---
# <a name="working-with-data-types-jdbc"></a>Arbeiten mit Datentypen (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Die Hauptfunktion von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] liegt darin, Java-Entwicklern den Zugriff auf Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken zu ermöglichen. Der JDBC-Treiber sorgt dazu für die Konvertierung zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen und Java-Typen und -Objekten.

> [!NOTE]
> Eine ausführliche Beschreibung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]- und JDBC-Treiberdatentypen, einschließlich deren Unterschiede und deren Konvertierung in Java-Datentypen, finden Sie unter [Grundlegendes zu den Datentypen des JDBC-Treibers](understanding-the-jdbc-driver-data-types.md).

Damit SQL Server-Datentypen verarbeitet werden können, enthält der JDBC-Treiber get\<Type>- und set\<Type>-Methoden für die Klassen [SQLServerPreparedStatement](reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](reference/sqlservercallablestatement-class.md) sowie get\<Type>- und update\<Type>-Methoden für die Klasse [SQLServerResultSet](reference/sqlserverresultset-class.md). Die verwendete Methode hängt vom Datentyp ab, der verarbeitet wird, sowie davon, ob Resultsets oder Abfragen verwendet werden.

Die Themen in diesem Abschnitt beschreiben, wie Sie in Java-Anwendungen unter Verwendung von JDBC-Treiberdatentypen auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Daten zugreifen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Thema|BESCHREIBUNG|
|-----------|-----------------|
|[Beispiel zu Standarddatentypen](basic-data-types-sample.md)|Beschreibt, wie Werte von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Standarddatentypen mithilfe von Abrufmethoden für Resultsets abgerufen und wie diese Werte mithilfe von Updatemethoden für Resultsets aktualisiert werden.|
|[Beispiel für den SQLXML-Datentyp](sqlxml-data-type-sample.md)|Beschreibt das Speichern von XML-Daten in einer relationalen Datenbank, das Abrufen von XML-Daten aus einer Datenbank sowie das Analysieren von XML-Daten mit dem Java-Datentyp **SQLXML**.|
|[Beispiel für räumliche Datentypen](spatial-data-types-sample.md)|In diesem Thema wird beschrieben, wie Sie Daten mit den räumlichen Datentypen „Geometrie“ und „Geografie“ in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mit den vom Microsoft JDBC-Treiber definierten Java-Typen **Geometry** und **Geography** speichern und wieder abrufen.|

## <a name="see-also"></a>Weitere Informationen

[Beispiele für JDBC-Treiberanwendungen](sample-jdbc-driver-applications.md)
