> sl.md sublime text usage tips

# Install Package Control in sublime text 2 or 3 [Ref](https://www.imjeff.cn/blog/62/)

## Through command line

    # sublime text 3
    import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())


    # sublime text 2
    import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')

## Manually by download package

1. Click Preferences > Browse Packages

2. Go to the upper level folder in the opened dialog window, then enter the Installed Packages folder.

3. Download [Package Control.sublime-package](https://sublime.wbond.net/Package%20Control.sublime-package) and copy to Installed Packages folder.

4. Restart sublime text.
