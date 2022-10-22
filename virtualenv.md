# virtualenv

## pre requiresties
1. Install virtualenv from pip with `pip install virtualenv`

## Create virtualenv in a project
1. use this command in your project directory
   
   ```bashe
   python3 -m virtualenv amooati_env
   ```

## Activate/Deactivate virtualenv
### Activation - Mac/Linux
```bashe
source amooati_env/bin/activate
```
### Activation - Windows
```bashe
.\amooati_env\Scripts\activate.bat
```

### Deactivation - Any OS
```bashe
deactivate
```

After activating this virtualenv, every package that you install will go to `amooati_env/lib/python-version/site-packages`

