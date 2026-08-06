# Exportador headless de datos vanilla

Esta variante mantiene el extractor de datos de Endstone, pero añade un comando de consola que funciona en Linux sin GLFW, ImGui, OpenGL, Xvfb, VNC ni escritorio remoto.

## Comando

Después de que BDS muestre `Server started.`, ejecuta en la consola:

```text
exportvanilla
```

Alias:

```text
exportdata
```

La recopilación se ejecuta en el hilo principal de BDS y los archivos se escriben en:

```text
<directorio-del-servidor>/data
```

Se generan:

```text
biomes.json
block_palette.nbt
block_states.json
block_tags.json
block_types.json
creative_groups.json
creative_items.nbt
item_components.nbt
item_tags.json
items.json
recipes.json
```

El comando solo puede utilizarse desde la consola.

## Compilar en Ubuntu

El proyecto utiliza Clang 20, libc++ y Ninja. Desde la raíz del código fuente:

```bash
sudo apt-get update
sudo apt-get install -y build-essential lsb-release wget software-properties-common gnupg python3-venv
wget -q https://apt.llvm.org/llvm.sh
chmod +x llvm.sh
sudo ./llvm.sh 20
sudo apt-get install -y libc++-20-dev libc++abi-20-dev clang-tools-20 ninja-build
sudo update-alternatives --install /usr/bin/clang clang /usr/bin/clang-20 200
sudo update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-20 200
```

Crea un entorno e instala el proyecto:

```bash
python3 -m venv .build-venv
source .build-venv/bin/activate
python -m pip install -U pip conan
python -m pip install -U . -C build-dir=./build
```

Para sustituir Endstone dentro de un bundle existente, activa el `.venv` de ese bundle y ejecuta la instalación desde esta carpeta de código fuente:

```bash
source /ruta/al/bundle/.venv/bin/activate
python -m pip install -U . -C build-dir=./build
```

Luego inicia el bundle normalmente con `start.sh`, espera `Server started.` y ejecuta `exportvanilla`.
