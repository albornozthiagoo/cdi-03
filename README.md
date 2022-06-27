Alumno:Thiago Albornoz 
Curso:4°1 Avionica 
Materia:Control de Interfaces 
Colaboradores:Sebastian Erbino Valenitn Franco

#include <stdio.h> #include <ctype.h> #include <math.h>

#define MAX 4096

int read_file(char *text, char *filename);

int main(int argc, char *argv[]) {

if (argc != 2) { printf("Uso: ./readability file\n"); return 1; }

char text[MAX];

if (read_file(text, argv[1])) { printf("Archivo no encontrado\n"); return 1; }

int L; int P; int S; int i = 0;

while (text[i]>0) {

if (text[i]=='.'|| text[i] == '?'|| text[i] == '!'){
    S++;
}

if (text[i]==' ') {
    P++; 
}

if (isalpha(text[i])) {
    L++;

}
} L=(100L/P); S=(100S/P); float index = 0.0588 * L - 0.296 * S - 15.8;
index = round(index);

if (index>16) { printf ("Grade 16+"); } else if (index<1) {

printf("Below Grade 1");}
else {
    printf("Grade %d", index);
}
return 0; } int read_file(char *text, char *filename) {

FILE *fp; char c; char full_name[30];

sprintf(full_name, "texts/%s.txt", filename); fp = fopen(full_name, "r");

if (!fp) { return 1; }

do { c = getc(fp); *text = c; text++; } while (c != EOF);

text--; *text = '\0';

return 0; }
