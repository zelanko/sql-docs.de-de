---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: abbdbeec81a029716ac6516f9436373e91365a23
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702772"
---
# <a name="using-ado-with-microsoft-visual-basic-and-visual-basic-for-applications"></a>Verwenden von ADO mit Microsoft Visual Basic und Visual Basic für Applikationen
Das Einrichten eines ADO-Projekts, und Schreiben von ADO-Code ist ähnlich, ob Sie Visual Basic oder Visual Basic für Applikationen verwenden. Dieses Thema behandelt das Verwenden von ADO mit Visual Basic und Visual Basic für Applikationen und Anmerkungen dieser Unterschiede.

## <a name="referencing-the-ado-library"></a>Verweis auf die ADO-Bibliothek
 Die ADO-Bibliothek muss vom Projekt verwiesen werden.

#### <a name="to-reference-ado-from-microsoft-visual-basic"></a>Auf ADO-Verweis aus Microsoft Visual Basic

1.  In Visual Basic aus der **Projekt** , wählen Sie im Menü **Verweise...** .

2.  Wählen Sie **Microsoft ActiveX Data Objects x.x Bibliothek** aus der Liste. Überprüfen Sie, ob mindestens die folgenden Bibliotheken werden ebenfalls ausgewählt:

    -   Visual Basic for Applications

    -   Visual Basic-Laufzeitobjekte und Prozeduren

    -   Visual Basic-Objekte und Prozeduren

    -   OLE-Automatisierung

3.  Klicken Sie auf **OK**.

 ADO können ganz einfach mit Visual Basic für Applikationen, mit Microsoft Access, z. B.

#### <a name="to-reference-ado-from-microsoft-access"></a>Auf ADO-Verweis aus Microsoft Access

1.  Klicken Sie in Microsoft Access wählen oder erstellen Sie ein Modul aus der **Module** Registerkarte die **Datenbank** Fenster.

2.  Auf der **Tools** , wählen Sie im Menü **Verweise...** .

3.  Wählen Sie **Microsoft ActiveX Data Objects x.x Bibliothek** aus der Liste. Überprüfen Sie, ob mindestens die folgenden Bibliotheken werden ebenfalls ausgewählt:

    -   Visual Basic for Applications

    -   Microsoft Access 8.0-Objektbibliothek (oder höher)

    -   Microsoft-DAO-3.5-Objektbibliothek (oder höher)

4.  Klicken Sie auf **OK**.

## <a name="creating-ado-objects-in-visual-basic"></a>Erstellen von ADO-Objekte in Visual Basic
 Um eine Automation-Variable und eine Instanz eines Objekts für die Variable zu erstellen, können Sie zwei Methoden verwenden: **Dim** oder **CreateObject**.

### <a name="dim"></a>Dim
 Können Sie die **neu** Schlüsselwort mit **Dim** deklarieren und Erstellen von Instanzen der ADO-Objekte in einem Schritt:

```
Dim conn As New ADODB.Connection
```

 Sie können auch die **Dim** Anweisung Deklaration und die Objekt-Instanziierung kann auch sein, zwei Schritte:

```
Dim conn As ADODB.Connection
Set conn = New ADODB.Connection
```

> [!NOTE]
>  Es ist nicht erforderlich, um explizit die `ADODB` mit progid der **Dim** -Anweisung, vorausgesetzt, Sie haben die ADO-Bibliothek ordnungsgemäß in Ihrem Projekt referenziert. Verwendung wird jedoch sichergestellt, dass Sie keine werden Namenskonflikte mit anderen Bibliotheken.

> [!NOTE]
>  Z. B. Wenn Sie Verweise auf ADO und DAO im selben Projekt einschließen, aufzunehmen einen Qualifizierer aus, um anzugeben, welches Objektmodell verwendet, bei der Instanziierung **Recordset** Objekte, wie im folgenden Code:

```
Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset
```

### <a name="createobject"></a>CreateObject
 Mit der **CreateObject** -Methode, die Deklaration und die Objekt-Instanziierung muss zwei separate Schritte:

```
Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object
```

 Instanziieren von Objekten mit **CreateObject** werden spät gebunden, d. h., die sie nicht stark typisiert und Befehlszeilen-Vervollständigung wurde deaktiviert. Allerdings erlaubt Ihnen, den Verweis auf die ADO-Bibliothek aus Ihrem Projekt zu überspringen und ermöglicht es Ihnen, bestimmte Versionen von Objekten zu instanziieren. Zum Beispiel:

```
Set conn1 = CreateObject("ADODB.Connection.2.0") As Object
```

 Sie können dies auch erreichen, indem speziell einen Verweis auf die ADO-Typbibliothek in der Version 2.0 und Erstellen des Objekts.

 Instanziieren von Objekten mithilfe der **CreateObject** Methode ist in der Regel langsamer als die Verwendung der **Dim** Anweisung.

## <a name="handling-events"></a>Behandeln von Ereignissen
 Um ADO-Ereignisse in Microsoft Visual Basic zu verarbeiten, müssen Sie deklarieren, einem auf Modulebene Variablen mithilfe der **WithEvents** Schlüsselwort. Die Variable kann nur als Teil eines Moduls Klasse deklariert werden und muss auf der Modulebene deklariert werden. Eine ausführlichere Erläuterung der ADO-Ereignisse behandeln, finden Sie unter [Handling ADO Events](../../../ado/guide/data/handling-ado-events.md).

## <a name="visual-basic-examples"></a>Visual Basic-Beispiele
 Viele Visual Basic-Beispiele sind in der ADO-Dokumentation enthalten. Weitere Informationen finden Sie unter [ADO-Codebeispiele in Microsoft Visual Basic](../../../ado/reference/ado-api/ado-code-examples-in-visual-basic.md).

## <a name="see-also"></a>Siehe auch
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md) [Verwenden von ADO mit Microsoft Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) [Verwenden von ADO mit Skriptsprachen](../../../ado/guide/appendixes/using-ado-with-scripting-languages.md)
