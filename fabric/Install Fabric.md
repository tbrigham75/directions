1.  First make sure Go is installed.  Look at directions for that in Go folder.
2. go install github.com/danielmiessler/fabric@latest

3.  Update:  vi ~/.bashrc and paste the below code in it: 


    #------------ For Fabric AI -----------------------
    # Golang environment variables
    export GOROOT=/usr/local/go/
    export GOPATH=$HOME/go
    export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin

    # Update PATH to include GOPATH and GOROOT binaries
    export PATH=$GOPATH/bin:$GOROOT/bin:$HOME/.local/bin:$PATH

    # Loop through all files in the ~/.config/fabric/patterns directory
    for pattern_file in $HOME/.config/fabric/patterns/*; do
        # Get the base name of the file (i.e., remove the directory path)
        pattern_name=$(basename "$pattern_file")

        # Create an alias in the form: alias pattern_name="fabric --pattern pattern_name"
        alias_command="alias $pattern_name='fabric --pattern $pattern_name'"

        # Evaluate the alias command to add it to the current shell
        eval "$alias_command"
    done

    yt() {
        local video_link="$1"
        fabric -y "$video_link" --transcript
4. source ~/.bashrc
5.  Updates are as simple as:  
    go install github.com/danielmiessler/fabric@latest