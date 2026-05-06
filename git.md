
################################################################################
# GIT & GITHUB - STEP BY STEP ANLEITUNG
# Arbeiten mit Git und GitHub über das Terminal inkl. Branch-Management
################################################################################

# ==============================================================================
# 1. INITIAL SETUP - Git Konfiguration
# ==============================================================================

# Git-Benutzername setzen (wird bei Commits angezeigt)
git config --global user.name "Dein Name"

# Git-E-Mail setzen (sollte mit deiner GitHub-E-Mail übereinstimmen)
git config --global user.email "deine.email@example.com"

# Standard-Editor festlegen (z.B. vim, nano, code)
git config --global core.editor "nano"

# Farbige Ausgabe aktivieren (bessere Lesbarkeit)
git config --global color.ui auto

# Aktuelle Git-Konfiguration anzeigen
git config --list


# ==============================================================================
# 2. NEUES REPOSITORY ERSTELLEN (Lokales Projekt)
# ==============================================================================

# Neues Verzeichnis für das Projekt erstellen
mkdir mein-projekt
cd mein-projekt

# Git-Repository initialisieren (erstellt versteckten .git Ordner)
git init

# Ersten Branch umbenennen zu "main" (moderner Standard statt "master")
git branch -M main

# Status des Repositories anzeigen (zeigt untracked/modified files)
git status


# ==============================================================================
# 3. EXISTIERENDES REPOSITORY KLONEN
# ==============================================================================

# Repository von GitHub klonen (HTTPS)
git clone https://github.com/username/repository-name.git

# Repository von GitHub klonen (SSH - benötigt SSH-Key Setup)
git clone git@github.com:username/repository-name.git

# Repository klonen und eigenen Ordnernamen vergeben
git clone https://github.com/username/repository-name.git mein-ordner

# Nach dem Klonen ins Verzeichnis wechseln
cd repository-name


# ==============================================================================
# 4. GRUNDLEGENDE GIT-BEFEHLE - Der Standard-Workflow
# ==============================================================================

# Neue Datei erstellen
echo "# Mein Projekt" > README.md

# Status anzeigen (README.md ist jetzt "untracked")
git status

# Datei zur Staging Area hinzufügen (bereit für Commit)
git add README.md

# ODER: Alle geänderten/neuen Dateien hinzufügen
git add .

# ODER: Bestimmte Dateitypen hinzufügen
git add *.js

# ODER: Interaktiv Dateien auswählen
git add -p

# Staged Changes anzeigen (was wird committed?)
git status

# Commit erstellen mit Nachricht
git commit -m "Initial commit: README hinzugefügt"

# ODER: Commit mit detaillierter Nachricht (öffnet Editor)
git commit

# ODER: Staging und Commit in einem Schritt (nur für tracked files)
git commit -am "Änderungen an bestehenden Dateien"

# Commit-Historie anzeigen
git log

# Kompakte Log-Ansicht (eine Zeile pro Commit)
git log --oneline

# Log mit grafischer Darstellung der Branches
git log --oneline --graph --all


# ==============================================================================
# 5. REMOTE REPOSITORY VERBINDEN (GitHub)
# ==============================================================================

# Remote Repository hinzufügen (Verbindung zu GitHub herstellen)
git remote add origin https://github.com/username/repository-name.git

# Alle Remote Repositories anzeigen
git remote -v

# Remote Repository umbenennen
git remote rename origin upstream

# Remote Repository entfernen
git remote remove origin

# Ersten Push durchführen und upstream setzen
git push -u origin main

# Nachfolgende Pushes (wenn upstream gesetzt ist)
git push


# ==============================================================================
# 6. ARBEITEN MIT BRANCHES - Das Herzstück
# ==============================================================================

# Alle lokalen Branches anzeigen (* markiert aktuellen Branch)
git branch

# Alle Branches inkl. Remote Branches anzeigen
git branch -a

# Neuen Branch erstellen
git branch feature-login

# Neuen Branch erstellen UND direkt wechseln (kombinierter Befehl)
git checkout -b feature-registrierung

# Zu einem Branch wechseln
git checkout feature-login

# ODER: Moderner Befehl zum Wechseln (ab Git 2.23)
git switch feature-login

# Neuen Branch erstellen und wechseln (moderner Befehl)
git switch -c feature-logout

# Aktuellen Branch anzeigen
git branch --show-current


# ==============================================================================
# 7. TYPISCHER FEATURE-BRANCH WORKFLOW
# ==============================================================================

# Szenario: Neues Feature entwickeln

# Schritt 1: Sicherstellen, dass main aktuell ist
git checkout main
git pull origin main

# Schritt 2: Neuen Feature-Branch erstellen
git checkout -b feature-user-profile

# Schritt 3: Änderungen vornehmen
echo "User Profile Code" > user-profile.js

# Schritt 4: Änderungen committen
git add user-profile.js
git commit -m "feat: User Profile Komponente hinzugefügt"

# Schritt 5: Weitere Änderungen (mehrere Commits möglich)
echo "mehr Code" >> user-profile.js
git commit -am "feat: Profil-Bearbeitung implementiert"

# Schritt 6: Branch zu GitHub pushen
git push -u origin feature-user-profile

# Schritt 7: Auf GitHub einen Pull Request erstellen
# (Dies geschieht im Browser auf github.com)


# ==============================================================================
# 8. BRANCHES ZUSAMMENFÜHREN (MERGING)
# ==============================================================================

# Variante A: Merge über GitHub Pull Request (Empfohlen)
# - Erstelle Pull Request auf GitHub
# - Code Review durchführen
# - Merge über GitHub Interface

# Variante B: Lokaler Merge

# Schritt 1: Zu main wechseln
git checkout main

# Schritt 2: Sicherstellen, dass main aktuell ist
git pull origin main

# Schritt 3: Feature-Branch in main mergen
git merge feature-user-profile

# Schritt 4: Merge zu GitHub pushen
git push origin main

# Fast-Forward Merge erzwingen (nur wenn keine neuen Commits auf main)
git merge --ff-only feature-user-profile

# Merge Commit erzwingen (auch bei Fast-Forward Möglichkeit)
git merge --no-ff feature-user-profile -m "Merge feature-user-profile"


# ==============================================================================
# 9. MERGE KONFLIKTE LÖSEN
# ==============================================================================

# Wenn beim Merge Konflikte auftreten:

# Schritt 1: Konflikt-Dateien identifizieren
git status

# Schritt 2: Konflikt-Dateien manuell bearbeiten
# Suche nach Konflikt-Markierungen:
# <<<<<<< HEAD
# Dein aktueller Code
# =======
# Code aus dem anderen Branch
# >>>>>>> feature-branch

# Schritt 3: Konfliktmarkierungen entfernen und entscheiden, was behalten wird
nano konflikt-datei.js

# Schritt 4: Gelöste Datei zur Staging Area hinzufügen
git add konflikt-datei.js

# Schritt 5: Merge abschließen
git commit -m "Merge Konflikt gelöst"

# ODER: Merge abbrechen und zum vorherigen Zustand zurück
git merge --abort


# ==============================================================================
# 10. REBASE - Alternative zu Merge (Fortgeschritten)
# ==============================================================================

# Rebase hält die Commit-Historie linear und sauber

# Schritt 1: Auf Feature-Branch wechseln
git checkout feature-user-profile

# Schritt 2: Rebase auf main
git rebase main

# Schritt 3: Bei Konflikten: Konflikte lösen, dann
git add .
git rebase --continue

# ODER: Rebase abbrechen
git rebase --abort

# Schritt 4: Force Push nach Rebase (überschreibt Remote History!)
git push -f origin feature-user-profile

# ACHTUNG: Force Push nur auf eigenen Feature-Branches, NIE auf main!


# ==============================================================================
# 11. BRANCH MANAGEMENT - Aufräumen
# ==============================================================================

# Branch lokal löschen (nur wenn bereits gemerged)
git branch -d feature-user-profile

# Branch lokal löschen (erzwingen, auch wenn nicht gemerged)
git branch -D feature-alte-idee

# Branch remote löschen (von GitHub entfernen)
git push origin --delete feature-user-profile

# Alle lokalen Branches anzeigen, die bereits gemerged wurden
git branch --merged

# Alle remote Branches anzeigen
git branch -r

# Verwaiste Remote-Tracking Branches entfernen (Cleanup)
git remote prune origin

# ODER: Automatisch beim Fetch
git fetch --prune


# ==============================================================================
# 12. ÄNDERUNGEN RÜCKGÄNGIG MACHEN
# ==============================================================================

# Unstaged Änderungen verwerfen (Datei zurücksetzen)
git checkout -- dateiname.js
# ODER moderner:
git restore dateiname.js

# Alle unstaged Änderungen verwerfen
git restore .

# Datei aus Staging Area entfernen (behält Änderungen)
git reset HEAD dateiname.js
# ODER moderner:
git restore --staged dateiname.js

# Letzten Commit rückgängig machen (Änderungen bleiben erhalten)
git reset --soft HEAD~1

# Letzten Commit rückgängig machen (Änderungen gehen verloren!)
git reset --hard HEAD~1

# Commit-Nachricht des letzten Commits ändern
git commit --amend -m "Neue Commit-Nachricht"

# Datei zum letzten Commit hinzufügen (ohne neue Commit-Nachricht)
git add vergessene-datei.js
git commit --amend --no-edit


# ==============================================================================
# 13. ZWISCHEN BRANCHES WECHSELN MIT UNGESPEICHERTEN ÄNDERUNGEN
# ==============================================================================

# Problem: Branch wechseln, aber Änderungen noch nicht committen möchten

# Lösung 1: Änderungen temporär speichern (Stash)
git stash

# Zu anderem Branch wechseln
git checkout other-branch

# Zurück zum ursprünglichen Branch
git checkout feature-branch

# Stash wieder anwenden
git stash pop

# Alle Stashes anzeigen
git stash list

# Bestimmten Stash anwenden
git stash apply stash@{0}

# Stash mit Nachricht erstellen
git stash save "WIP: Login-Formular halb fertig"

# Stash löschen
git stash drop stash@{0}


# ==============================================================================
# 14. REMOTE REPOSITORY UPDATES - PULL & FETCH
# ==============================================================================

# Änderungen von GitHub holen UND mergen (fetch + merge)
git pull origin main

# Nur Änderungen holen, OHNE zu mergen
git fetch origin

# Alle Branches von allen Remotes holen
git fetch --all

# Nach fetch: Remote Changes anzeigen
git log HEAD..origin/main

# Nach fetch: Unterschiede anzeigen
git diff HEAD origin/main

# Pull mit Rebase statt Merge (hält Historie linear)
git pull --rebase origin main


# ==============================================================================
# 15. BRANCHES VERGLEICHEN
# ==============================================================================

# Unterschiede zwischen zwei Branches anzeigen
git diff main..feature-branch

# Nur Dateinamen anzeigen, die unterschiedlich sind
git diff --name-only main..feature-branch

# Commits anzeigen, die in feature-branch aber nicht in main sind
git log main..feature-branch

# Grafische Darstellung der Branch-Divergenz
git log --oneline --graph main feature-branch


# ==============================================================================
# 16. NÜTZLICHE ALIASES EINRICHTEN
# ==============================================================================

# Shortcuts für häufige Befehle erstellen

git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.lg 'log --oneline --graph --all --decorate'

# Nutzung: git st statt git status


# ==============================================================================
# 17. .gitignore - DATEIEN VOM TRACKING AUSSCHLIESSEN
# ==============================================================================

# .gitignore Datei erstellen
cat > .gitignore << EOF
# Node.js
node_modules/
npm-debug.log

# Environment Variables
.env
.env.local

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Build
dist/
build/
*.log
EOF

# .gitignore committen
git add .gitignore
git commit -m "chore: .gitignore hinzugefügt"


# ==============================================================================
# 18. BEST PRACTICES & TIPPS
# ==============================================================================

# Commit-Nachricht Konventionen (Conventional Commits):
# feat: Neues Feature
# fix: Bugfix
# docs: Dokumentation
# style: Formatierung
# refactor: Code-Umstrukturierung
# test: Tests
# chore: Wartungsaufgaben

# Beispiele:
git commit -m "feat: Benutzer-Authentifizierung implementiert"
git commit -m "fix: Login-Button funktioniert jetzt auf Mobile"
git commit -m "docs: API-Dokumentation erweitert"

# Branch-Naming Konventionen:
# feature/feature-name
# bugfix/issue-beschreibung
# hotfix/critical-bug
# release/version-nummer

# Beispiele:
git checkout -b feature/user-authentication
git checkout -b bugfix/login-error
git checkout -b hotfix/security-patch


# ==============================================================================
# 19. GITHUB WORKFLOW - KOMPLETTES BEISPIEL
# ==============================================================================

# Tag 1: Projekt Setup
git clone https://github.com/username/project.git
cd project
git checkout -b feature/neue-funktion

# Tag 2-3: Entwicklung
echo "Code" > neue-datei.js
git add neue-datei.js
git commit -m "feat: Neue Funktion Basis implementiert"
git push -u origin feature/neue-funktion

# Tag 4: Weitere Commits
git commit -am "feat: Neue Funktion erweitert"
git push

# Tag 5: Main ist updated, Änderungen übernehmen
git checkout main
git pull origin main
git checkout feature/neue-funktion
git rebase main  # ODER: git merge main
git push -f      # Nach Rebase nötig

# Tag 6: Pull Request erstellen auf GitHub

# Tag 7: Nach Code Review und Merge
git checkout main
git pull origin main
git branch -d feature/neue-funktion
git push origin --delete feature/neue-funktion


# ==============================================================================
# 20. TROUBLESHOOTING - HÄUFIGE PROBLEME
# ==============================================================================

# Problem: "Your branch is ahead of 'origin/main' by X commits"
# Lösung:
git push origin main

# Problem: "Your branch is behind 'origin/main'"
# Lösung:
git pull origin main

# Problem: "rejected - non-fast-forward"
# Lösung: Pull vor Push
git pull origin main
git push origin main

# Problem: Versehentlich auf main committed statt auf Feature-Branch
# Lösung: Commit in neuen Branch verschieben
git branch feature-branch-name
git reset HEAD~1 --hard
git checkout feature-branch-name

# Problem: SSH Authentifizierung fehlgeschlagen
# Lösung: SSH Key generieren und zu GitHub hinzufügen
ssh-keygen -t ed25519 -C "deine.email@example.com"
cat ~/.ssh/id_ed25519.pub  # Diesen Key zu GitHub hinzufügen

# Problem: Große Dateien committen
# Lösung: Git LFS (Large File Storage) verwenden
git lfs install
git lfs track "*.psd"
git add .gitattributes


################################################################################
# ENDE DER ANLEITUNG
#
# Weitere Ressourcen:
# - Git Documentation: https://git-scm.com/doc
# - GitHub Guides: https://guides.github.com/
# - Interactive Git Learning: https://learngitbranching.js.org/
#
# Tipp: Übe diese Befehle in einem Test-Repository, bevor du sie in
#       produktiven Projekten einsetzt!
################################################################################
