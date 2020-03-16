# nginx-sticky-module

Open ngx_http_sticky_misc.c then 

gmtime_r(&t, &e); // keep if using on linux
gmtime_s(&t, &e);   // keep if using on windows