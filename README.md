This script downloads wallpapers from <a href="http://wallhaven.cc" target="_blank">wallhaven.cc</a>, the script offers various filter options to download only wallpapers to your liking.

You can configure it directly inside the script or per command line arguments (command line arguments will override settings made directly in the script)
check `./wallhaven.sh -h` for details

<h3>This Script is written for GNU Linux, it should work under Mac OS</h3>

Dependencies:
- bash
- wget
- sed
- jq
- gnu parallel (if you wish to use it)
### 用法
Usage: ./wallhaven.sh [OPTIONS]
Download wallpapers from wallhaven.cc

If no options are specified, default values from within the script will be used

 -l, --location		图片存放地址 location where the wallpapers will be stored
 -n, --number		下载数量 Number of Wallpapers to download
 -s, --startpage	开始页数，终端时继续下载使用 page to start downloading from
 -t, --type		Type of download Operation: standard, search,
            collections, useruploads
 -c, --categories	下载类型，三个数字分别代表通用、动画、人物，1 包含，0 排除，都要就 111 ，只要人物就 001 。categories to download from, eg. 111 for General,
            Anime and People, 1 to include, 0 to exclude
 -f, --filter		过滤露骨程度，三个数字分别代表 SFW 、sketchy 、NSFW ，SFW 表示 Safe For Work ，NSFW 表示 Not Safe For Work ，sketchy 居中。filter out content based on purity rating, eg. 111
            for SFW, sketchy and NSFW content, 1 to include,
            0 to exclude
 -r, --resolution	目标分辨率，多个分辨率使用英文逗号分隔。resolutions to download, separate mutliple
            resolutions by ,
 -g, --atleast		最小分辨率。不能与-r 同时使用。minimum resolution, show all images with a
            resolution greater than the specified value
            do not use in combination with -r (--resolution)
 -a, --aspectratio	分辨率对比度，例如 16x9 或 16x10 。要下手机壁纸可以用 9x16 。only download wallpaper with given aspectratios,
            separate multiple aspectratios by ,
 -m, --mode		排序方式。sorting mode for wallpapers: relevance, random,
            date_added, views, favorites
 -o, --order		顺序 asc 还是逆序 desc 。order ascending (asc) or descending (desc)
 -b, --collection	name of the collections to download
 -q, --query		search query, eg. 'mario', single quotes needed,
            for searching exact phrases use double quotes
            inside single quotes, eg. '"super mario"'
 -d, --dye, --color	search for wallpapers containing the given color,
            color values are RGB without a leading #
 -u, --user		download wallpapers from given user
 -p, --parallel		使用 gnu parallel 来多线程下载。make use of gnu parallel (1 to enable, 0 to disable)
 -v, --version		show current version
 -h, --help		显示帮助信息。show this help text and exit

Examples:
./wallhaven.sh	-l ~/wp/ -n 48 -s 1 -t standard -c 101 -f 111 -r 1920x1080
        -a 16x9 -m random -o desc -p 1

Download 48 random wallpapers with a resolution of 1920x1080 and
an aspectratio of 16x9 to ~/wp/ starting with page 1 from the
categories general and people including SFW, sketchy and NSWF Content
while utilizing gnu parallel

./wallhaven.sh	-l ~/wp/ -n 48 -s 1 -t search -c 111 -f 100 -r 1920x1080 -a 16x9
        -m relevance -o desc -q '"super mario"' -d cc0000 -p 1

Download 48 wallpapers related to the search query "super mario" containing
the color #cc0000 with a resolution of 1920x1080 and an aspectratio of 16x9
to ~/wp/ starting with page 1 from the categories general, anime and people,
including SFW Content and excluding sketchy and NSWF Content while utilizing
gnu paralle
