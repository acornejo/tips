# Customize-XSession

Create a startup script:

    cat << EOF > /etc/X11/Xsession.d/15mystart
    #!/bin/bash
    # To force gnome interface in open office
    # export OOO_FORCE_DESKTOP=gnome
    test -d "$HOME/.bin" && export PATH="$HOME/.bin:$PATH"
    if [ -d "$HOME/.latex" ]; then
        export TEXINPUTS=.:$HOME/.latex:
        export BSTINPUTS=$TEXINPUTS
        export BIBINPUTS=$TEXINPUTS
    fi
    EOF
