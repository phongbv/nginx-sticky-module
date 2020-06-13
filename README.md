# nginx-sticky-module
Open ngx_http_sticky_misc.c then 

gmtime_r(&t, &e); // keep if using on linux
gmtime_s(&t, &e);   // keep if using on windows

For windows
1. Open the "Developer Command Prompt for VS2015". Run "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\vcvars32.bat".
2. Run "C:\MinGW\msys\1.0\msys.bat" to open the MINGW32 environment.

auto/configure \
--with-cc=cl \
--with-debug \
--prefix= \
--conf-path=conf/nginx.conf \
--pid-path=logs/nginx.pid \
--http-log-path=logs/access.log \
--error-log-path=logs/error.log \
--sbin-path=nginx.exe \
--with-stream \
--with-stream_ssl_module \
--with-http_realip_module \
--http-client-body-temp-path=temp/client_body_temp \
--http-proxy-temp-path=temp/proxy_temp \
--http-fastcgi-temp-path=temp/fastcgi_temp \
--http-scgi-temp-path=temp/scgi_temp \
--http-uwsgi-temp-path=temp/uwsgi_temp \
--with-cc-opt=-DFD_SETSIZE=1024 \
--with-pcre=objs/lib/pcre-8.44 \
--with-zlib=objs/lib/zlib-1.2.11 \
--with-openssl=objs/lib/openssl-1.1.1d \
--with-openssl-opt=no-asm \
--with-http_ssl_module \
--with-stream_ssl_preread_module \
--add-module=nginx-sticky-module-ng

On Windows: 
- Open objs/Makefile
- Remove "-W4 -WX" in this line CFLAGS =  -O2  -W4 -WX -nologo -MT -Zi -Fdobjs/nginx.pdb -DFD_SETSIZE=1024 -DNO_SYS_TYPES_H
- Run "nmake"

On Linux:
- Run "make"
- Run "make install"
