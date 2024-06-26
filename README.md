# Ejercicio de migración parte 2

## Migración a objetos

### Objetivo

Incorporar el paradigma de programación orientada a objetos (OOP) y transformar la aplicación en una aplicación en
Streamlit
para favorcer la mantenibilidad del código fuente.

## Código original

* Ver el código fuente del proyecto https://github.com/shakamoushie/pixmatch/blob/main/pixmatch.py . Este proyecto tiene
  un clone del proyecto original
* Interactuar con el juego para entener las funcionalidades principales https://pixmatchgame.streamlit.app
* Instalar el proyecto en su computador local. Escriba desde la línea de comandos y ubicado en la carpeta raíz del
  proyecto `pip install -r requirements.txt`. Note que si no tiene un ambiente virtual primero debe configurarlo.
* Ejecutar el juego localmente. Escriba en consola `streamlit run pixmatch.py`. Su navegador debería abrir el juego
  ![img.png](docs/img/ejecucion.png)

## Pendientes

El proyecto tiene la siguiente estructura de directorios:

1. Documentar las clases y métodos que se han creado
2. Genera documentación que explique la estructura de directorios de este proyecto
3. Completar código fuente para lograr funcionalidad completa del juego

## Por hacer
1. Intente correr el proyecto, identifique el script que inicia la interacción y ejecute el compato streamlit run `nombre.py`
2. Debe ver algo como lo siguiente ![img.png](docs/img/ejecucion_poo_template.png)
3. Inicie la migración iniciando por el radio button de las dificultades


## Diagrama del proyecto
```mermaid
classDiagram
    class GameController {
        -selected_difficulty
        -current_player
        -emoji_bank
        -target_emoji
        -game_status
        -board
        +define_player()
        +pick_emoji_bank()
        +choose_sidebar_emoji()
        +find_target_emoji()
        +pre_new_game()
        +new_game()
        +reset_game()
        +verify_game_status()
        +play()
    }
    class GUIController {
        -game_controller
        -run_page
        +main()
        +read_picture_file()
        +verify_pressed_cell()
    }
    class Board {
        -cells_map
        -expired_cells_list
        -board_size
        +update_cell()
        +reset_board()
    }
    class BoardCell {
        -cell_idx
        -verification_result
        -row = 0
        -col = 0
        -emoji_img
        -emoji_index 
    }
    class LeaderBoardManager {
        +create_leader_board(player)
        +read_leader_board(player)
        +update_leader_board(player, MAX_PLAYERS)()
    }
    class Player {
        -player_name_country
        -score
        
        + Player(player_name_country)
    }
    class MainView {
        +draw_main_page()
        +draw_main_board()
    }
    class App {
        +main()
    }
    GUIController --> GameController : has
    Board <-- GameController : has
    Board o-- BoardCell : has
    GameController --> Player : has
    GameController --> LeaderBoardManager : uses
    LeaderBoardManager ..> Player : usesa
    MainView ..> GameController : uses
    GUIController ..> MainView : uses
    App ..> GUIController : launches

```
Editor:https://diagrams.helpful.dev/s/s:MAdFfNUs