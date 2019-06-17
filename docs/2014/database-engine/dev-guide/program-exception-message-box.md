---
title: Programmieren von Ausnahmemeldungsfeld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 316afc6d5f3a87ff7431240681066ac5ee66ede6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62780695"
---
# <a name="program-exception-message-box"></a>Programmieren eines Ausnahmemeldungsfelds
  Mit dem Ausnahmemeldungsfeld können Sie in Ihren Anwendungen das Verhalten von Meldungen erheblich besser bestimmen als mit der <xref:System.Windows.Forms.MessageBox>-Klasse. Weitere Informationen finden Sie unter [Ausnahme Message Box-Programmierung](../../../2014/database-engine/dev-guide/exception-message-box-programming.md). Weitere Informationen zum Abrufen und Bereitstellen der DLL-Assembly für das Ausnahmemeldungsfeld finden Sie unter [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a>So behandeln Sie eine Ausnahme mit dem Ausnahmemeldungsfeld  
  
1.  Fügen Sie einen Verweis auf die Microsoft.ExceptionMessageBox.dll-Assembly in das Projekt mit verwaltetem Code ein.  
  
2.  (Optional) Hinzufügen einer `using` (c#) oder `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) Richtlinie mit den <xref:Microsoft.SqlServer.MessageBox> Namespace.  
  
3.  Erstellen Sie einen try/catch-Block, um die erwartete Ausnahme zu behandeln.  
  
4.  Erstellen Sie innerhalb des `catch`-Blocks eine Instanz der <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>-Klasse. Übergeben Sie die <xref:System.Exception> Objekt behandelt, indem die `try` - `catch` Block.  
  
5.  (Optional) Legen Sie eine oder mehrere der folgenden Eigenschaften für <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> fest:  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> Enumeration, die im Ausnahmemeldungsfeld anzuzeigenden Schaltflächen angibt.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> Enumeration, der die Standardschaltfläche für das Ausnahmemeldungsfeld angibt.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> Enumeration, die zum Steuern anderer Verhalten des ausnahmemeldungsfelds verwendet wird.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> Enumeration, die das Symbol für die Anzeige im Ausnahmemeldungsfeld angibt.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>-Methode auf. Übergeben Sie das übergeordnete Fenster, zu dem das Ausnahmemeldungsfeld gehört.  
  
7.  (Optional) Beachten Sie den Wert des zurückgegebenen <xref:System.Windows.Forms.DialogResult> Enumeration, die bei Bedarf, um zu bestimmen, welche Schaltfläche der Benutzer geklickt haben.  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a>So zeigen Sie das Ausnahmemeldungsfeld ohne Ausnahme an  
  
1.  Fügen Sie einen Verweis auf die Microsoft.ExceptionMessageBox.dll-Assembly in das Projekt mit verwaltetem Code ein.  
  
2.  (Optional) Hinzufügen einer `using` (c#) oder `Imports` -Anweisung (Visual Basic .NET) verwenden die <xref:Microsoft.SqlServer.MessageBox> Namespace.  
  
3.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> -Klasse. Übergeben Sie den Meldungstext als <xref:System.String>-Wert.  
  
4.  (Optional) Legen Sie eine oder mehrere der folgenden Eigenschaften für <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> fest:  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> Enumeration, die im Ausnahmemeldungsfeld anzuzeigenden Schaltflächen angibt.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - Dialogfeldbeschriftung des Ausnahmemeldungsfelds.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> Enumeration, der die Standardschaltfläche für das Dialogfeld des ausnahmemeldungsfelds angibt.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> Enumeration, die zum Steuern anderer Verhalten des ausnahmemeldungsfelds verwendet wird.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> Enumeration, die das Symbol für die Anzeige im Ausnahmemeldungsfeld angibt.  
  
5.  Rufen Sie die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>-Methode auf. Übergeben Sie das übergeordnete Fenster, zu dem das Ausnahmemeldungsfeld gehört.  
  
6.  (Optional) Notieren Sie den Wert der zurückgegebenen <xref:System.Windows.Forms.DialogResult>-Enumeration, wenn Sie bestimmen müssen, auf welche Schaltfläche der Benutzer geklickt hat.  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a>So zeigen Sie das Ausnahmemeldungsfeld mit benutzerdefinierten Schaltflächen an  
  
1.  Fügen Sie einen Verweis auf die Microsoft.ExceptionMessageBox.dll-Assembly in das Projekt mit verwaltetem Code ein.  
  
2.  (Optional) Hinzufügen einer `using` (c#) oder `Imports` -Anweisung (Visual Basic .NET) verwenden die <xref:Microsoft.SqlServer.MessageBox> Namespace.  
  
3.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>-Klasse. Hierzu haben Sie zwei Möglichkeiten:  
  
    -   Übergeben Sie die <xref:System.Exception> Objekt behandelt, indem eine `try` - `catch` Block.  
  
    -   Übergeben Sie den Meldungstext als <xref:System.String>-Wert.  
  
4.  Legen Sie für <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> einen der folgenden Werte fest:  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> -Zeigt die **Abbrechen**, **wiederholen**, und **ignorieren** Schaltflächen.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - zeigt benutzerdefinierte Schaltflächen an.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> -Zeigt die **OK** Schaltfläche.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> -Zeigt die **OK** und **Abbrechen** Schaltflächen.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> -Zeigt die **wiederholen** und **Abbrechen** Schaltflächen.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> -Zeigt **Ja** und **keine** Schaltflächen.  
  
    -   <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> -Zeigt **Ja**, **keine**, und **Abbrechen** Schaltflächen.  
  
5.  (Optional) Wenn Sie benutzerdefinierte Schaltflächen verwenden, rufen Sie eine der Überladungen der <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A>-Methode auf, um Text für bis zu fünf benutzerdefinierte Schaltflächen anzugeben.  
  
6.  Rufen Sie die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>-Methode auf. Übergeben Sie das übergeordnete Fenster, zu dem das Ausnahmemeldungsfeld gehört.  
  
7.  (Optional) Notieren Sie den Wert der zurückgegebenen <xref:System.Windows.Forms.DialogResult>-Enumeration, wenn Sie bestimmen müssen, auf welche Schaltfläche der Benutzer geklickt hat. Wenn Sie benutzerdefinierte Schaltflächen verwenden, notieren Sie den Wert von <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> für die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A>-Eigenschaft, um zu ermitteln, auf welche benutzerdefinierte Schaltfläche der Benutzer geklickt hat.  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a>So ermöglichen Sie Benutzern die Entscheidung darüber, ob das Ausnahmemeldungsfeld angezeigt werden soll  
  
1.  Fügen Sie einen Verweis auf die Microsoft.ExceptionMessageBox.dll-Assembly in das Projekt mit verwaltetem Code ein.  
  
2.  (Optional) Hinzufügen einer `using` (c#) oder `Imports` -Anweisung (Visual Basic .NET) verwenden die <xref:Microsoft.SqlServer.MessageBox> Namespace.  
  
3.  Erstellen Sie eine Instanz der <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>-Klasse. Hierzu haben Sie zwei Möglichkeiten:  
  
    -   Übergeben Sie die <xref:System.Exception> Objekt behandelt, indem eine `try` - `catch` Block.  
  
    -   Übergeben Sie den Meldungstext als <xref:System.String>-Wert.  
  
4.  Legen Sie die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> -Eigenschaft auf `true`fest.  
  
5.  (Optional) Geben Sie den Text an, mit dem der Benutzer aufgefordert wird, zu entscheiden, ob das Ausnahmemeldungsfeld für <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A> erneut angezeigt werden soll. Der Standardtext lautet: "Diese Meldung nicht mehr anzeigen."  
  
6.  Wenn die Entscheidung des Benutzers nur für die Dauer der Anwendungsausführung gültig sein soll, legen Sie den Wert von <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> auf eine globale <xref:System.Boolean>-Variable fest. Werten Sie diesen Wert aus, bevor Sie eine Instanz des Ausnahmemeldungsfelds erstellen.  
  
7.  Wenn Sie die Entscheidung eines Benutzers dauerhaft speichern müssen, gehen Sie wie folgt vor:  
  
    1.  Rufen Sie die CreateSubKey-Methode auf, um einen von Ihrer Anwendung verwendeten benutzerdefinierten Registrierungsschlüssel zu öffnen, und legen Sie <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> auf das zurückgegebene RegistryKey-Objekt fest.  
  
    2.  Legen Sie <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> auf den Namen des verwendeten Registrierungswerts fest.  
  
    3.  Legen Sie <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> auf `true` fest.  
  
    4.  Rufen Sie die <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A>-Methode auf. Der angegebene Registrierungsschlüssel wird ausgewertet, und das Ausnahmemeldungsfeld wird nur angezeigt, wenn die im Registrierungsschlüssel gespeicherten Daten 0 sind. Wenn das Dialogfeld angezeigt wird und der Benutzer das Kontrollkästchen aktiviert, bevor er auf eine Schaltfläche klickt, werden die Daten im Registrierungsschlüssel auf 1 gesetzt.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet das Ausnahmemeldungsfeld nur mit der **OK** Schaltfläche, um Informationen von einer Anwendungsausnahme anzuzeigen, die die behandelte Ausnahme sowie zusätzliche anwendungsspezifische Informationen enthält.  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet das Ausnahmemeldungsfeld mit **Ja** und **keine** Schaltflächen aus dem der Benutzer auswählt.  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das Ausnahmemeldungsfeld mit benutzerdefinierten Schaltflächen verwendet.  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das Kontrollkästchen verwendet, um zu bestimmen, ob das Ausnahmemeldungsfeld angezeigt werden soll.  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden das Kontrollkästchen und ein Registrierungsschlüssel verwendet, um zu bestimmen, ob das Ausnahmemeldungsfeld angezeigt werden soll.  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das Ausnahmemeldungsfeld verwendet, um weitere Informationen anzuzeigen, die bei der Problembehandlung oder beim Debuggen hilfreich sein können.  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
