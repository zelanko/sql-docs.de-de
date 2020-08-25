---
description: Verwenden von ADO mit Microsoft Visual Basic und Visual Basic for Applications
title: Verwenden von ADO mit Microsoft Visual Basic | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, Visual Basic
- Visual Basic [ADO]
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
author: rothja
ms.author: jroth
ms.openlocfilehash: efb206f3c0fbbeb0fbc700f8e714ddd1d5ee5a8c
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806519"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Verwenden von ADO mit Microsoft Visual Basic und Visual Basic for Applications
Das Einrichten eines ADO-Projekts und das Schreiben von ADO-Code ist ähnlich, egal ob Sie Visual Basic oder Visual Basic for Applications verwenden. In diesem Thema wird die Verwendung von ADO mit Visual Basic und Visual Basic for Applications erläutert, und es werden alle Unterschiede erläutert.

## <a name="referencing-the-ado-library"></a>Verweisen auf die ADO-Bibliothek
 Auf die ADO-Bibliothek muss von Ihrem Projekt verwiesen werden.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>So verweisen Sie auf ADO von Microsoft Visual Basic

1.  Wählen Sie in Visual Basic im Menü **Projekt** die Option **Verweise...** aus.

2.  Wählen Sie in der Liste **Microsoft ActiveX Data Objects x. x-Bibliothek** aus. Vergewissern Sie sich, dass mindestens die folgenden Bibliotheken ausgewählt sind:

    -   Visual Basic for Applications

    -   Visual Basic Runtime-Objekte und Prozeduren

    -   Visual Basic von Objekten und Prozeduren

    -   OLE-Automatisierung

3.  Klicken Sie auf **OK**.

 Sie können ADO ebenso problemlos mit Visual Basic for Applications verwenden, beispielsweise mithilfe von Microsoft Access.

#### <a name="to-reference-ado-from-microsoft-access"></a>So verweisen Sie auf ADO von Microsoft Access

1.  Wählen Sie in Microsoft Access im **Daten Bank** Fenster auf der Registerkarte **Module** ein Modul aus, oder erstellen Sie es.

2.  Wählen Sie **im Menü Extras** die Option **Verweise...** aus.

3.  Wählen Sie in der Liste **Microsoft ActiveX Data Objects x. x-Bibliothek** aus. Vergewissern Sie sich, dass mindestens die folgenden Bibliotheken ausgewählt sind:

    -   Visual Basic for Applications

    -   Microsoft Access 8,0-Objektbibliothek (oder höher)

    -   Microsoft DAO 3,5-Objektbibliothek (oder höher)

4.  Klicken Sie auf **OK**.

## <a name="creating-ado-objects-in-visual-basic"></a>Erstellen von ADO-Objekten in Visual Basic
 Zum Erstellen einer Automatisierungs Variablen und einer Instanz eines Objekts für diese Variable können Sie zwei Methoden verwenden: **Dim** oder **kreateobject**.

### <a name="dim"></a>Dim
 Sie können das **New** -Schlüsselwort mit **Dim** verwenden, um Instanzen von ADO-Objekten in einem Schritt zu deklarieren und zu erstellen:

```
Dim conn As New ADODB.Connection
```

 Alternativ können auch die Deklaration der **Dim** -Anweisung und die Objekt Instanziierung zwei Schritte sein:

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Es ist nicht erforderlich `ADODB` , die ProgID explizit mit der **Dim** -Anweisung zu verwenden, vorausgesetzt, Sie haben die ADO-Bibliothek im Projekt ordnungsgemäß referenziert. Durch die Verwendung von wird jedoch sichergestellt, dass keine Namenskonflikte mit anderen Bibliotheken auftreten.

> [!NOTE]
>  Wenn Sie z. b. Verweise auf ADO und DAO in dasselbe Projekt einschließen, sollten Sie einen Qualifizierer einschließen, um anzugeben, welches Objektmodell beim Instanziieren von **recordsetobjekten** verwendet werden soll, wie im folgenden Code gezeigt:

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 Bei der Methode " **kreateobject** " müssen die Deklaration und die Objekt Instanziierung zwei diskrete Schritte sein:

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Objekte, die mit " **kreateobject** " instanziiert werden, sind spät gebunden, was bedeutet, dass Sie nicht stark typisiert sind und die Befehlszeilen Vervollständigung deaktiviert ist. Allerdings können Sie mit dem Verweis auf die ADO-Bibliothek aus dem Projekt überspringen und bestimmte Versionen von Objekten instanziieren. Beispiel:

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 Dies können Sie auch durchführen, indem Sie speziell einen Verweis auf die Typbibliothek der ADO-Version 2,0 erstellen und das Objekt erstellen.

 Das Instanziieren von Objekten mithilfe **der Methode "** Methode" ist in der Regel langsamer als die Verwendung der **Dim** -Anweisung.

## <a name="handling-events"></a>Behandeln von Ereignissen
 Um ADO-Ereignisse in Microsoft Visual Basic verarbeiten zu können, müssen Sie eine Variable auf Modulebene mithilfe des **widervents** -Schlüssel Worts deklarieren. Die Variable kann nur als Teil eines Klassen Moduls deklariert werden und muss auf Modulebene deklariert werden. Eine ausführlichere Erläuterung der Behandlung von ADO-Ereignissen finden Sie unter [Behandeln von ADO](../data/handling-ado-events.md)-Ereignissen.

## <a name="visual-basic-examples"></a>Visual Basic Beispiele
 Viele Visual Basic Beispiele sind in der ADO-Dokumentation enthalten. Weitere Informationen finden Sie unter [ADO-Code Beispiele in Microsoft Visual Basic](../../reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>Weitere Informationen
 [Microsoft ActiveX Data Objects (ADO)](../../microsoft-activex-data-objects-ado.md) [Verwenden von ADO mit Microsoft Visual C++](./using-ado-with-microsoft-visual-c.md) [mithilfe von ADO und Skriptsprachen](./using-ado-with-scripting-languages.md)