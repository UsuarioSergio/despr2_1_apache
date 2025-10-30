# despr2_1_apache
Habilitar una pagina de apache con su navegacion entre distintas paginas y sus imagenes

## Eliminar antiguas reglas de puertos

VBoxManage modifyvm "Ubuntu-Apache-A2-1" --natpf1 delete "ssh"
VBoxManage modifyvm "Ubuntu-Apache-A2-1" --natpf1 delete "http"
VBoxManage modifyvm "Ubuntu-Apache-A2-1" --natpf1 delete "https"

## Crear nuevas reglas con puertos diferentes

VBoxManage modifyvm "Ubuntu-Apache-A2-1" --natpf1 "ssh,tcp,,2223,,22"
VBoxManage modifyvm "Ubuntu-Apache-A2-1" --natpf1 "http,tcp,,8081,,80"
VBoxManage modifyvm "Ubuntu-Apache-A2-1" --natpf1
"https,tcp,,8444,,443"

## Pasos para instalar y visualizar el contenido que se queria mostar de apache
Se entra a la maquina por el puerto 2223 ya que se modifico, se actualiza y instala apache2 

sudo ufw allow 'Apache Full', esto se hace para que permita http y https el firewall aparte de los que ya tenia

" scp -P 2223 -r Downloads/ejemplo_sitio_apache/ dawserver@localhost:~/practicas/apache  " Se copian los archivos en la vm y se moverian al directorio "/var/www/html" tras haberlo limpiado

Comprobación de que están los archivos en el directorio donde se suele encontrar los documentos que se muestran:
<img width="621" height="331" alt="image" src="https://github.com/user-attachments/assets/a5e505b3-2e36-4d1f-9ae5-b8705a254d24" />


Por ultimo se comprobaria si al entrar en la pagina "http:localhost:8081" porque se habia cambiado:
<img width="933" height="706" alt="image" src="https://github.com/user-attachments/assets/c5904b81-520e-4bf8-a611-cc610f590b5c" />

Y por último se muestra que pasa si entras a otra parte de la página:
<img width="802" height="439" alt="image" src="https://github.com/user-attachments/assets/567a53b0-8277-40c1-b23b-53cd79305d11" />
