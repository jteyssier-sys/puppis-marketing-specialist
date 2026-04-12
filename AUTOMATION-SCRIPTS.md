# 🤖 Automation Scripts - Adaptar Skills Rápido

**Scripts bash y PowerShell para automáticamente adaptar skills de Puppis a cualquier otro cliente en minutos**

---

## 📦 Script 1: Setup Completo (Puppis → Tu Cliente)

### Opción A: macOS/Linux

Guarda este archivo como `setup-new-client.sh`:

```bash
#!/bin/bash

# SETUP: Adaptar Puppis Marketing Specialist para nuevo cliente
# Uso: ./setup-new-client.sh "MiCliente" "@micliente_ar" "@micliente_co"

set -e  # Exit on error

# Colores para output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m'  # No Color

# Variables de entrada
CLIENT_NAME="${1:?Error: Proporciona nombre de cliente}"
HANDLE_AR="${2:?Error: Proporciona handle Argentina}"
HANDLE_CO="${3:?Error: Proporciona handle Colombia}"

echo -e "${BLUE}========================================${NC}"
echo -e "${BLUE}Adaptando Puppis Skills para ${CLIENT_NAME}${NC}"
echo -e "${BLUE}========================================${NC}"
echo ""

# 1. Renombrar archivos
echo -e "${YELLOW}[1/5] Renombrando archivos...${NC}"
find . -name "*puppis*" -type f | while read file; do
    new_file=$(echo "$file" | sed "s/puppis/${CLIENT_NAME,,}/g")
    mv "$file" "$new_file" 2>/dev/null || true
    echo -e "${GREEN}✓${NC} $file → $new_file"
done
echo ""

# 2. Reemplazar "Puppis" con nombre del cliente
echo -e "${YELLOW}[2/5] Reemplazando 'Puppis' con '${CLIENT_NAME}'...${NC}"
find . -name "*.md" -type f -exec sed -i '' \
    -e "s/Puppis/${CLIENT_NAME}/g" \
    -e "s/puppis/${CLIENT_NAME,,}/g" \
    {} +
echo -e "${GREEN}✓${NC} Reemplazado"
echo ""

# 3. Reemplazar handles de redes sociales
echo -e "${YELLOW}[3/5] Actualizando handles de redes sociales...${NC}"
find . -name "*.md" -type f -exec sed -i '' \
    -e "s/@puppisarg/${HANDLE_AR}/g" \
    -e "s/@puppiscol/${HANDLE_CO}/g" \
    -e "s/@PuppisColombia/@${HANDLE_CO#@}/g" \
    {} +
echo -e "${GREEN}✓${NC} Handles actualizados"
echo ""

# 4. Crear estructura de carpetas
echo -e "${YELLOW}[4/5] Creando estructura de carpetas...${NC}"
mkdir -p skills guides templates examples docs .github/workflows
echo -e "${GREEN}✓${NC} Carpetas creadas"
echo ""

# 5. Mover archivos a carpetas
echo -e "${YELLOW}[5/5] Organizando archivos...${NC}"
mv *-SKILL.md skills/ 2>/dev/null || true
mv *-GUIDE.md guides/ 2>/dev/null || true
mv SETUP*.md docs/ 2>/dev/null || true
echo -e "${GREEN}✓${NC} Archivos organizados"
echo ""

# Resumen final
echo -e "${GREEN}========================================${NC}"
echo -e "${GREEN}✅ SETUP COMPLETADO${NC}"
echo -e "${GREEN}========================================${NC}"
echo ""
echo "Cliente: ${CLIENT_NAME}"
echo "Handle Argentina: ${HANDLE_AR}"
echo "Handle Colombia: ${HANDLE_CO}"
echo ""
echo "Próximos pasos:"
echo "1. Revisa manualmente los archivos"
echo "2. Edita ejemplos específicos del industry"
echo "3. git add ."
echo "4. git commit -m 'feat: Adapt for ${CLIENT_NAME}'"
echo "5. git push origin main"
echo ""
```

**Usa así:**

```bash
# Dale permisos
chmod +x setup-new-client.sh

# Ejecuta
./setup-new-client.sh "LunaFashion" "@lunafashion_ar" "@lunafashion_co"

# Output:
# ========================================
# Adaptando Puppis Skills para LunaFashion
# ========================================
# [1/5] Renombrando archivos...
# ✓ puppis-marketing-specialist-SKILL.md → lunafashion-marketing-specialist-SKILL.md
# ...
# ✅ SETUP COMPLETADO
```

---

### Opción B: Windows (PowerShell)

Guarda como `setup-new-client.ps1`:

```powershell
# SETUP: Adaptar Puppis Marketing Specialist para nuevo cliente
# Uso: .\setup-new-client.ps1 -ClientName "MiCliente" -HandleAR "@micliente_ar" -HandleCO "@micliente_co"

param(
    [Parameter(Mandatory=$true)]
    [string]$ClientName,
    
    [Parameter(Mandatory=$true)]
    [string]$HandleAR,
    
    [Parameter(Mandatory=$true)]
    [string]$HandleCO
)

Write-Host "========================================" -ForegroundColor Cyan
Write-Host "Adaptando Puppis Skills para $ClientName" -ForegroundColor Cyan
Write-Host "========================================" -ForegroundColor Cyan
Write-Host ""

# 1. Renombrar archivos
Write-Host "[1/5] Renombrando archivos..." -ForegroundColor Yellow
Get-ChildItem -Filter "*puppis*" -Recurse | ForEach-Object {
    $newName = $_.Name -replace "puppis", $ClientName.ToLower()
    Rename-Item -Path $_.FullName -NewName $newName -Force
    Write-Host "✓ $($_.Name) → $newName" -ForegroundColor Green
}
Write-Host ""

# 2. Reemplazar "Puppis" con nombre del cliente
Write-Host "[2/5] Reemplazando 'Puppis' con '$ClientName'..." -ForegroundColor Yellow
Get-ChildItem -Filter "*.md" -Recurse | ForEach-Object {
    $content = Get-Content $_.FullName
    $content = $content -replace "Puppis", $ClientName
    $content = $content -replace "puppis", $ClientName.ToLower()
    Set-Content -Path $_.FullName -Value $content
}
Write-Host "✓ Reemplazado" -ForegroundColor Green
Write-Host ""

# 3. Reemplazar handles
Write-Host "[3/5] Actualizando handles de redes sociales..." -ForegroundColor Yellow
Get-ChildItem -Filter "*.md" -Recurse | ForEach-Object {
    $content = Get-Content $_.FullName
    $content = $content -replace "@puppisarg", $HandleAR
    $content = $content -replace "@puppiscol", $HandleCO
    Set-Content -Path $_.FullName -Value $content
}
Write-Host "✓ Handles actualizados" -ForegroundColor Green
Write-Host ""

# 4. Crear carpetas
Write-Host "[4/5] Creando estructura de carpetas..." -ForegroundColor Yellow
@("skills", "guides", "templates", "examples", "docs", ".github/workflows") | ForEach-Object {
    New-Item -ItemType Directory -Force -Path $_ | Out-Null
}
Write-Host "✓ Carpetas creadas" -ForegroundColor Green
Write-Host ""

# 5. Mover archivos
Write-Host "[5/5] Organizando archivos..." -ForegroundColor Yellow
Get-ChildItem -Filter "*-SKILL.md" | Move-Item -Destination "skills/" -Force
Get-ChildItem -Filter "*-GUIDE.md" | Move-Item -Destination "guides/" -Force
Write-Host "✓ Archivos organizados" -ForegroundColor Green
Write-Host ""

# Resumen
Write-Host "========================================" -ForegroundColor Green
Write-Host "✅ SETUP COMPLETADO" -ForegroundColor Green
Write-Host "========================================" -ForegroundColor Green
Write-Host ""
Write-Host "Cliente: $ClientName"
Write-Host "Handle Argentina: $HandleAR"
Write-Host "Handle Colombia: $HandleCO"
Write-Host ""
Write-Host "Próximos pasos:"
Write-Host "1. Revisa manualmente los archivos"
Write-Host "2. Edita ejemplos específicos del industry"
Write-Host "3. git add ."
Write-Host "4. git commit -m 'feat: Adapt for $ClientName'"
Write-Host "5. git push origin main"
```

**Usa así:**

```powershell
# Dale permisos (una sola vez)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Ejecuta
.\setup-new-client.ps1 -ClientName "LunaFashion" -HandleAR "@lunafashion_ar" -HandleCO "@lunafashion_co"
```

---

## 🔧 Script 2: Búsqueda y Reemplazo Avanzado

### Para Reemplazos Complejos

Guarda como `advanced-replace.sh`:

```bash
#!/bin/bash

# ADVANCED REPLACE: Reemplaza múltiples términos en bulk
# Uso: ./advanced-replace.sh

# Define mapeo de reemplazos
declare -A REPLACE_MAP=(
    ["Puppis"]="LunaFashion"
    ["puppisarg"]="lunafashion_ar"
    ["puppiscol"]="lunafashion_co"
    ["pet retail"]="e-commerce fashion"
    ["alimento mascotas"]="ropa + accesorios"
    ["dueños de mascotas"]="clientes fashion-conscious"
    ["41 sucursales Argentina"]="25 tiendas Argentina"
    ["36 sucursales Colombia"]="18 tiendas Colombia"
    ["Puppis Club"]="Luna VIP"
    ["puntos por compra"]="credits por compra"
)

echo "Ejecutando reemplazos complejos..."
echo ""

# Itera sobre mapeo
for search in "${!REPLACE_MAP[@]}"; do
    replace="${REPLACE_MAP[$search]}"
    echo "Buscando: '$search' → Reemplazando por: '$replace'"
    
    # Reemplaza en todos los .md
    find . -name "*.md" -type f -exec sed -i '' \
        -e "s/${search}/${replace}/g" \
        {} +
    
    echo "✓ Done"
done

echo ""
echo "✅ Todos los reemplazos completados"
```

**Usa así:**

```bash
chmod +x advanced-replace.sh
./advanced-replace.sh
```

---

## 📊 Script 3: Verificación de Calidad

### Verifica que Reemplazos Fueron Correctos

Guarda como `verify-changes.sh`:

```bash
#!/bin/bash

# VERIFY: Chequea que los cambios se hicieron correctamente

echo "Verificando cambios..."
echo ""

# 1. Busca si quedan referencias a "Puppis" (debería haber 0)
echo "[1] Buscando referencias residuales a 'Puppis'..."
PUPPIS_COUNT=$(grep -r "Puppis" . --include="*.md" 2>/dev/null | wc -l)
if [ $PUPPIS_COUNT -eq 0 ]; then
    echo "✅ OK: No hay referencias a 'Puppis'"
else
    echo "⚠️  WARNING: Encontrados $PUPPIS_COUNT referencias a 'Puppis' (debería ser 0)"
    grep -r "Puppis" . --include="*.md" | head -5
fi
echo ""

# 2. Verifica estructura de carpetas
echo "[2] Verificando estructura de carpetas..."
if [ -d "skills" ] && [ -d "guides" ] && [ -d "docs" ]; then
    echo "✅ OK: Carpetas existen"
    echo "   - skills: $(find skills -name "*.md" | wc -l) archivos"
    echo "   - guides: $(find guides -name "*.md" | wc -l) archivos"
    echo "   - docs: $(find docs -name "*.md" | wc -l) archivos"
else
    echo "⚠️  WARNING: Faltan carpetas"
fi
echo ""

# 3. Verifica que no hay archivos vacíos
echo "[3] Verificando archivos vacíos..."
EMPTY=$(find . -name "*.md" -size 0)
if [ -z "$EMPTY" ]; then
    echo "✅ OK: No hay archivos vacíos"
else
    echo "⚠️  WARNING: Archivos vacíos encontrados: $EMPTY"
fi
echo ""

# 4. Cuenta total de archivos
echo "[4] Resumen..."
TOTAL=$(find . -name "*.md" | wc -l)
TOTAL_SIZE=$(du -sh . | awk '{print $1}')
echo "✅ Total de archivos .md: $TOTAL"
echo "✅ Tamaño total: $TOTAL_SIZE"
echo ""

echo "✅ Verificación completa"
```

**Usa así:**

```bash
chmod +x verify-changes.sh
./verify-changes.sh

# Output:
# Verificando cambios...
# [1] Buscando referencias residuales a 'Puppis'...
# ✅ OK: No hay referencias a 'Puppis'
# ...
# ✅ Verificación completa
```

---

## 🚀 Script 4: Automatizar Commit + Push

### Hace commit y push automáticamente

Guarda como `commit-and-push.sh`:

```bash
#!/bin/bash

# COMMIT & PUSH: Automatiza el flujo git

CLIENT_NAME="${1:?Error: Proporciona nombre de cliente}"

echo "Preparando para commit..."
echo ""

# 1. Verifica status
echo "[1] Verificando cambios pendientes..."
git status
echo ""

# 2. Add all
echo "[2] Agregando archivos..."
git add .
echo "✓ Archivos agregados"
echo ""

# 3. Commit
echo "[3] Creando commit..."
git commit -m "feat: Adapt Puppis Marketing Specialist for ${CLIENT_NAME}

- Replace brand context (Puppis → ${CLIENT_NAME})
- Update market info and locations
- Customize social media handles
- Adapt examples to industry
- Update tone and positioning
- Organize files in folders (skills, guides, templates, docs)

Marketing Specialist v2.0
Fecha: $(date '+%Y-%m-%d')"

echo "✓ Commit creado"
echo ""

# 4. Push
echo "[4] Subiendo a GitHub..."
git push origin main
echo "✓ Push completado"
echo ""

echo "✅ Listo para compartir con tu equipo"
echo ""
echo "Link: github.com/$(git config user.name)/${CLIENT_NAME,,}-marketing-specialist"
```

**Usa así:**

```bash
chmod +x commit-and-push.sh
./commit-and-push.sh "LunaFashion"

# Output:
# Preparando para commit...
# [1] Verificando cambios pendientes...
# [2] Agregando archivos...
# ✓ Archivos agregados
# [3] Creando commit...
# ✓ Commit creado
# [4] Subiendo a GitHub...
# ✓ Push completado
# ✅ Listo para compartir con tu equipo
```

---

## 🎯 Script 5: Pipeline Completo (Todo en Uno)

### Ejecuta todos los pasos en orden

Guarda como `full-setup-pipeline.sh`:

```bash
#!/bin/bash

# FULL PIPELINE: Setup completo en un comando

set -e

CLIENT_NAME="${1:?Error: Proporciona nombre de cliente}"
HANDLE_AR="${2:?Error: Proporciona handle Argentina (ej: @micliente_ar)}"
HANDLE_CO="${3:?Error: Proporciona handle Colombia (ej: @micliente_co)}"

echo -e "\n🚀 FULL SETUP PIPELINE\n"
echo "Cliente: $CLIENT_NAME"
echo "Argentina: $HANDLE_AR"
echo "Colombia: $HANDLE_CO"
echo ""

# Step 1: Setup
echo "========== STEP 1/4: SETUP =========="
bash ./setup-new-client.sh "$CLIENT_NAME" "$HANDLE_AR" "$HANDLE_CO"
echo ""

# Step 2: Advanced Replace
echo "========== STEP 2/4: ADVANCED REPLACE =========="
bash ./advanced-replace.sh
echo ""

# Step 3: Verify
echo "========== STEP 3/4: VERIFY =========="
bash ./verify-changes.sh
echo ""

# Step 4: Commit & Push
echo "========== STEP 4/4: COMMIT & PUSH =========="
read -p "¿Continuamos con commit y push? (s/n) " -n 1 -r
echo
if [[ $REPLY =~ ^[Ss]$ ]]; then
    bash ./commit-and-push.sh "$CLIENT_NAME"
else
    echo "Commit y push cancelados. Puedes hacerlo manualmente luego."
fi

echo ""
echo "========================================="
echo "✅ PIPELINE COMPLETADO"
echo "========================================="
echo ""
echo "Tu repositorio está listo:"
echo "https://github.com/$(git config user.name)/${CLIENT_NAME,,}-marketing-specialist"
```

**Usa así:**

```bash
chmod +x full-setup-pipeline.sh
./full-setup-pipeline.sh "LunaFashion" "@lunafashion_ar" "@lunafashion_co"

# Sigue las instrucciones interactivas
```

---

## 📋 Cheat Sheet: Todos los Comandos

```bash
# 1. Quick setup
./setup-new-client.sh "MiCliente" "@cliente_ar" "@cliente_co"

# 2. Advanced replace
./advanced-replace.sh

# 3. Verify quality
./verify-changes.sh

# 4. Commit + Push
./commit-and-push.sh "MiCliente"

# 5. Todo en uno
./full-setup-pipeline.sh "MiCliente" "@cliente_ar" "@cliente_co"
```

---

## 🎁 Bonus: Pre-commit Hook (Verificación Automática)

Evita commits con errores. Guarda como `.git/hooks/pre-commit`:

```bash
#!/bin/bash

echo "🔍 Pre-commit check..."

# Chequea que no haya referencias a "puppis" (case-insensitive)
if grep -ri "puppis" --include="*.md" . 2>/dev/null | grep -v ".git" > /dev/null; then
    echo "❌ ERROR: Aún hay referencias a 'Puppis' en archivos"
    echo "   Corrígelas antes de hacer commit"
    exit 1
fi

# Chequea que no haya archivos vacíos
if find . -name "*.md" -size 0 2>/dev/null | grep -v ".git"; then
    echo "❌ ERROR: Hay archivos vacíos"
    exit 1
fi

echo "✅ Pre-commit checks passed"
exit 0
```

**Usa así:**

```bash
chmod +x .git/hooks/pre-commit

# Ahora, cada vez que hagas `git commit`, se ejecuta automáticamente
# Si hay problemas, commit falla y te lo avisa
```

---

## 💻 Windows Batch (Si No Tienes PowerShell)

```batch
@echo off
REM SETUP para Windows (sin PowerShell)

setlocal enabledelayedexpansion

if "%~1"=="" (
    echo Error: Proporciona nombre de cliente
    exit /b 1
)

set CLIENT_NAME=%~1
set HANDLE_AR=%~2
set HANDLE_CO=%~3

echo.
echo Adaptando para %CLIENT_NAME%...
echo.

REM Renombra archivos (requiere PowerShell o herramienta externa)
powershell -Command "(ls *puppis* -Recurse) | %% {mv $_.FullName ($_.Name -replace 'puppis','%CLIENT_NAME%')}"

echo.
echo ✅ Setup completado para %CLIENT_NAME%
echo Handle AR: %HANDLE_AR%
echo Handle CO: %HANDLE_CO%
echo.
```

---

## 🆘 Troubleshooting Scripts

```bash
# Si script no ejecuta:
chmod +x *.sh

# Si sed da error (macOS vs Linux):
# macOS: sed -i '' 's/old/new/g'
# Linux: sed -i 's/old/new/g'

# Si Git falla:
git config user.name "Tu Nombre"
git config user.email "tu@email.com"

# Ver qué hace sed antes de ejecutar
sed -n 's/Puppis/LunaFashion/p' archivo.md
```

---

## ✅ Workflow Recomendado

1. **Descargá scripts en raíz del repo**
2. **Ejecutá pipeline completo:**
   ```bash
   ./full-setup-pipeline.sh "TuCliente" "@tucliente_ar" "@tucliente_co"
   ```
3. **Verifica manualmente** (abre archivos, chequea ejemplos)
4. **Commit + Push** (hecho automático por script)
5. **Comparte link** con equipo

**Tiempo total: 5 minutos** (vs. 1-2 horas haciendo todo manual)

---

*Automation Scripts v1.0*  
*Compatible: macOS, Linux, Windows (PowerShell)*
