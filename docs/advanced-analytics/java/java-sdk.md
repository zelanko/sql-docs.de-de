---
title: SDK für Java-Erweiterung – SQL Server-Spracherweiterungen
description: Beschreibung der Erweiterbarkeit, Microsoft SDK für Java für Microsoft SQL Server 2019
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fd050a5120f14b4727b93a74c1f46392ac24dd49
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759097"
---
# <a name="microsoft-extensibility-sdk-for-java-for-sql-server"></a>Erweiterungen für Microsoft-SDK für Java für SQLServer

In SQL Server CTP-Version 2.5 können Sie ein Java-Programm für SQL Server mithilfe des Microsoft-Erweiterungen-SDK für Java implementieren. Dies ist eine Schnittstelle für die Erweiterung der Java-Sprache, die zum Austauschen von Daten mit SQL Server und zum Ausführen von Java-Code von SQL Server verwendet wird.

> [!Note]
> Das SDK in der CTP-Version 2.5 ist eine große Änderung gegenüber früheren CTPs. Mussten Sie funktionierende Beispiele müssen aktualisiert werden, um das SDK verwenden.

Herunterladen der [Microsoft SDK für Java für Microsoft SQL Server-Erweiterbarkeit](http://aka.ms/mssql-java-lang-extension).

## <a name="implementation-requirements"></a>Implementierungsanforderungen

Die SDK-Schnittstelle definiert einen Satz von Anforderungen, die für SQL Server für die Kommunikation mit der Java Runtime erfüllt werden müssen. Dies bedeutet, dass Sie einige Regeln Implementierung in Ihrer main-Klasse entsprechen müssen. SQL Server können Sie eine bestimmte Methode in den Java-Klasse und Exchange Daten mithilfe der Java-spracherweiterung auszuführen.

Ein Beispiel, wie Sie das SDK verwenden können, finden Sie unter den [End-to-End-Beispiel](java-first-sample.md).

## <a name="sdk-classes"></a>SDK-Klassen

Dieses SDK besteht aus drei Klassen.

Zwei abstrakte Klassen, die definieren, die die Erweiterung für die Java-Schnittstelle verwendet, um die exchange-Daten mit SQL Server:

- **AbstractSqlServerExtensionExecutor**
- **AbstractSqlServerExtensionDataset**

Die dritte Klasse ist eine Hilfsklasse, die eine Implementierung eines DataSet-Objekts enthält. Dies ist eine optionale Klasse zu verwenden, um für den Einstieg erleichtern. Sie können Ihre eigene Implementierung einer solchen Klasse verwenden.

- **PrimitiveDataset**

Nachstehend werden die Details und der Quellcode für jede Klasse in der Java-Sprache-Erweiterung für SQL Server.

## <a name="abstractsqlserverextensionexecutor"></a>AbstractSqlServerExtensionExecutor

Dies ist eine abstrakte Klasse, die die Schnittstelle zum Ausführen von Java-Code von der Java-Sprache-Erweiterung für SQL Server enthält.

Die Java-Hauptklasse muss von dieser Klasse erben. Von dieser Klasse erben bedeutet, dass es bestimmte Methoden in der Klasse, die in Ihrer eigenen Klasse implementiert werden müssen.

Um von dieser abstrakten Klasse erben, erweitern Sie mit dem Namen der abstrakten Klasse in der Klassendeklaration:

```java
public class <MyClass> extends AbstractSqlServerExtensionExecutor {}
```

Zumindest muss die Hauptklasse die execute(...)-Methode zu implementieren.

### <a name="method-execute"></a>Führen Sie die Methode

Die Execute-Methode ist die Methode, die von SQL Server über die Erweiterung der Java-Sprache, zum Aufrufen von Java-Code von SQL Server aufgerufen wird. Zeigen Sie dies als eine wichtige Methode, bei denen Sie den Hauptknoten enthalten Vorgänge, die von SQL Server ausgeführt werden sollen.

Um Methodenargumente auf Java aus SQL Server zu übergeben, verwenden die `@param` Parameter in Sp_execute_external_script. Die Methode **ausführen** akzeptiert die Argumente auf diese Weise.

```java
public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params)  {}
```

### <a name="method-init"></a>Methode init

Die Init-Methode wird nach dem Konstruktor und vor der Execute-Methode ausgeführt. Alle Vorgänge, die vor dem execute(...) ausgeführt werden müssen, können bei dieser Methode erfolgen.

```java
public void init(String sessionId, int taskId, int numtask) {}
```

### <a name="abstractsqlserverextensionexecutor-source-code"></a>AbstractSqlServerExtensionExecutor-Quellcode

Weitere Informationen im Quellcode finden Sie weiter unten:

```java
package com.microsoft.sqlserver.javalangextension;

import java.lang.UnsupportedOperationException;

/**
 * Abstract class containing interface for handling input and output data used by the Java
 * extension.
 */
public class AbstractSqlServerExtensionDataset {
    /**
     * Column metadata interfaces
     */
    public void addColumnMetadata(int columnId, String columnName, int columnType, int precision, int scale) {
        throw new UnsupportedOperationException("addColumnMetadata is not implemented");
    }

    public int getColumnCount() {
        throw new UnsupportedOperationException("getColumnCount is not implemented");
    }

    public String getColumnName(int columnId) {
        throw new UnsupportedOperationException("getColumnName is not implemented");
    }

    public int getColumnPrecision(int columnId) {
        throw new UnsupportedOperationException("getColumnPrecision is not implemented");
    }

    public int getColumnScale(int columnId) {
        throw new UnsupportedOperationException("getColumnScale is not implemented");
    }

    public int getColumnType(int columnId) {
        throw new UnsupportedOperationException("getColumnNullMap is not implemented");
    }

    public boolean[] getColumnNullMap(int columnId) {
        throw new UnsupportedOperationException("getColumnNullMap is not implemented");
    }

    /**
     * Adding column interfaces
     */
    public void addIntColumn(int columnId, int[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addIntColumn is not implemented");
    }

    public void addBooleanColumn(int columnId, boolean[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addBooleanColumn is not implemented");
    }

    public void addLongColumn(int columnId, long[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addLongColumn is not implemented");
    }

    public void addFloatColumn(int columnId, float[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addFloatColumn is not implemented");
    }

    public void addDoubleColumn(int columnId, double[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addDoubleColumn is not implemented");
    }

    public void addShortColumn(int columnId, short[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addShortColumn is not implemented");
    }

    public void addStringColumn(int columnId, String[] rows) {
        throw new UnsupportedOperationException("addStringColumn is not implemented");
    }

    public void addBinaryColumn(int columnId, byte[][] rows) {
        throw new UnsupportedOperationException("addBinaryColumn is not implemented");
    }

    /**
     * Retrieving column interfaces
     */
    public int[] getIntColumn(int columnId) {
        throw new UnsupportedOperationException("getIntColumn is not implemented");
    }

    public long[] getLongColumn(int columnId) {
        throw new UnsupportedOperationException("getLongColumn is not implemented");
    }

    public float[] getFloatColumn(int columnId) {
        throw new UnsupportedOperationException("getFloatColumn is not implemented");
    }

    public short[] getShortColumn(int columnId) {
        throw new UnsupportedOperationException("getShortColumn is not implemented");
    }

    public boolean[] getBooleanColumn(int columnId) {
        throw new UnsupportedOperationException("getBooleanColumn is not implemented");
    }

    public double[] getDoubleColumn(int columnId) {
        throw new UnsupportedOperationException("getDoubleColumn is not implemented");
    }

    public String[] getStringColumn(int columnId) {
        throw new UnsupportedOperationException("getStringColumn is not implemented");
    }

    public byte[][] getBinaryColumn(int columnId) {
        throw new UnsupportedOperationException("getBinaryColumn is not implemented");
    }
}
```

### <a name="primitivedataset"></a>PrimitiveDataset

Diese Klasse ist eine Implementierung von **AbstractSqlServerExtensionDataset** , einfache Typen als Arrays von primitiven Datentypen speichert. Es wird im SDK einfach als unterstützende Klasse bereitgestellt, verwenden Sie optional ist.

Wenn Sie nicht diese Klasse verwenden, müssen Sie eine eigene Klasse implementieren, die von erbt **AbstractSqlServerExtensionDataset**.  

```java
package com.microsoft.sqlserver.javalangextension;

import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionDataset;
import java.lang.IllegalArgumentException;
import java.util.HashMap;
import java.util.Map;
import java.util.Map.Entry;

/**
 * Implementation of AbstractSqlServerExtensionDataset that stores
 * simple types as primitives arrays
 */
public class PrimitiveDataset extends AbstractSqlServerExtensionDataset {
    Map<Integer, String>  columnNames;
    Map<Integer, Integer> columnTypes;
    Map<Integer, Integer> columnPrecisions;
    Map<Integer, Integer> columnScales;
    Map<Integer, Object>  columns;
    Map<Integer, boolean[]> columnNullMaps;

    public PrimitiveDataset() {
        columnTypes = new HashMap<>();
        columnNames = new HashMap<>();
        columnPrecisions = new HashMap<>();
        columnScales = new HashMap<>();
        columns = new HashMap<>();
        columnNullMaps = new HashMap<>();
    }

    /**
     * Column metadata interfaces. Metadata is stored in a hash map, using the column ID as the key
     */
    public void addColumnMetadata(int columnId, String columnName, int sqlType, int precision, int scale) {
        if (columnTypes.containsKey(columnId))
        {
            throw new IllegalArgumentException("Metadata for column ID #: " + columnId + " already exists");
        }

        columnTypes.put(columnId, sqlType);
        columnNames.put(columnId, columnName);
        columnPrecisions.put(columnId, precision);
        columnScales.put(columnId, scale);
    }

    public int getColumnCount() {
        return columnTypes.size();
    }

    public String getColumnName(int columnId) {
        checkColumnMetadata(columnId);
        return columnNames.get(columnId);
    }

    public int getColumnPrecision(int columnId) {
        checkColumnMetadata(columnId);
        return columnPrecisions.get(columnId).intValue();
    }

    public int getColumnScale(int columnId) {
        checkColumnMetadata(columnId);
        return columnScales.get(columnId).intValue();
    }

    public int getColumnType(int columnId) {
        checkColumnMetadata(columnId);
        return columnTypes.get(columnId).intValue();
    }

    public boolean[] getColumnNullMap(int columnId) {
        checkColumnMetadata(columnId);
        return columnNullMaps.get(columnId);
    }

    /**
     * Adding column data interfaces. Column data is stored in a hash map, using the column ID as the key and
     * an array of the corresponding type representing each row. Primitives cannot be null, thus null values
     * are represented by an additional boolean array containing a flag to indicate if that value is null.
     * A null indicator array indicates that there are no null values in that column.
     */
    public void addIntColumn(int columnId, int[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addBooleanColumn(int columnId, boolean[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    };

    public void addLongColumn(int columnId, long[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addFloatColumn(int columnId, float[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addDoubleColumn(int columnId, double[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addShortColumn(int columnId, short[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addStringColumn(int columnId, String[] rows) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
    }

    public void addBinaryColumn(int columnId, byte[][] rows) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
    }

    /**
     * Retreiving column data interfaces. For primitive types, calling getColumnNullMap() for the column ID
     * will return the boolean array indicating null values.
     */
    public int[] getIntColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (int[])columns.get(columnId);
    }

    public long[] getLongColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (long[])columns.get(columnId);
    }

    public float[] getFloatColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (float[])columns.get(columnId);
    }

    public short[] getShortColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (short[])columns.get(columnId);
    }

    public boolean[] getBooleanColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (boolean[])columns.get(columnId);
    }

    public double[] getDoubleColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (double[])columns.get(columnId);
    }

    public String[] getStringColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (String[])columns.get(columnId);
    }

    public byte[][] getBinaryColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (byte[][])columns.get(columnId);
    }

    private void checkColumnMetadata(int columnId)
    {
        if (!columnTypes.containsKey(columnId)) {
            throw new IllegalArgumentException("Metadata for column ID #: " + columnId + " does not exist");
        }
    }
}
```

## <a name="next-steps"></a>Nächste Schritte

+ [End-to-end von Java-Beispiel mit dem SDK](java-first-sample.md)
+ [Gewusst wie: Aufrufen von Java in SQL Server](howto-call-java-from-sql.md)
+ [Java-Erweiterungen in SQL Server](extension-java.md)
+ [Java und SQL Server-Datentypen](java-sql-datatypes.md)
