---
ms.openlocfilehash: d2519b1cc56081f8a35308ac41e11f46a7f97211
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68215604"
---
1. **Erstellen Sie auf allen Servern mit SQL Server eine Server-Anmeldung für Pacemaker**. Die folgende Transact-SQL erstellt eine Anmeldung:

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

  Zum Zeitpunkt der Erstellung der verfügbarkeitsgruppe wird der Pacemaker-Benutzer ALTER, CONTROL und VIEW DEFINITION-Berechtigungen für die verfügbarkeitsgruppe, erfordern, nachdem es erstellt wurde, aber bevor alle Knoten hinzugefügt werden.

1. **Speichern Sie auf allen Servern mit SQL Server die Anmeldeinformationen für die SQL Server-Anmeldung**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
