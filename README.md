# 1
create files: file1...file1000: for i in {1..1000}; do touch "file${i}"; done
only 2 digits: ls -d file[0-9][0-9]
only "9": ls -d *[^0-9]*9[^0-9]*
except "1","4","7": ls -d *[!147]*

create directories: mkdir -p dir{1..100} && touch dir{1..100}/file{1..1000}

files with combinations: touch {'A','\', '$', '4'}{'A','\', '$', '4'}{'A','\', '$', '4'}{'A','\', '$', '4'}

files with extension combinations: touch file.{t,T}{x,X}{t,T}

# 2
clear tmp: find "$HOME/tmp" -mindepth 1 -type f -delete

conditional touch: if [ ! -e "foobar" ]; then touch "toto"; else touch "titi"; fi

size of file from full path: stat -c %s "$(cat foo/bar)"

evaluate 2**10000: echo '2^10000' | bc | tee value.txt

# 3
evaluate equation from variable: x=$((4+7)); echo > $x.txt;

write environment variables: printenv > env.txt;

change aliases: alias date='printenv"; alias printenv='date';

name of 1st directory from path variable: echo $PATH | cut -d ':' -f 1

evaluate arithmetic of numbers from files: result=$(($(<n1.txt) + $(<n2.txt) / $(<n3.txt))); echo $result;

# 4
create nondeletable file: touch "$HOME/temp/file.txt" && chmod +r+w "$HOME/temp/file.txt"

no display directory but display file: mkdir -m 711 -p "$HOME/titi" && touch "$HOME/titi/toto" && chmod 644 "$HOME/titi/toto"

open last modified by vi: vi "$(ls -t | head -n1)"

generate random 12 chars: tr -dc '[:graph:]' < /dev/urandom | fold -w 12 | head -n 1

# 5
display N number of symbol lines: grep -x ".\{N\}" toto

display real number lines: grep -E '[0-9]+\.[0-9]+' toto

sed without GID: sed 's/:[^:]*//' /etc/passwd

delete from 1st to windows: sed -i '1,/Windows/d' toto

write date to .bak: sed "1i$(date)" toto > toto.bak



