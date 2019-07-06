# Rangkuman_Modul2

Stacks adalah satu struktur data dimana penambahan dan penghapusan data, hanya dapat dilakukan pada satu ujung yang sama,
atau yang biasa dikenal dengan istilah top. karena samakin jauh posisi data dari top maka data tersebut diindikasikan
berada di stack lebih lama dibandingkan dengan data yang berada dekat pada data di posisi top.

Terdapat operasi dasar pada Stacks,
- stack () adalah inisialisasi stack yang kosong
- push(data) adalah penambahan data baru pada posisi top dari stack
- pop()adalah penghapusan data yang terdapat di posisi top dari stack.

Sedangkan return value dari fungsi ini adalah data yang dihapus dari stack tersebut
- peek() adalah informasi data yang terletak pada posisi top
- isEmpty() adalah untuk memeriksa apakah stack dalam keadaan kosong
- size() adalah informasi jumlah data yang terdapat pada stack

      def stack():
          s=[]
          return (s)
      def push(s,data):
          s.append(data)
      def pop(s):
          data=s.pop()
          return(data)
      def peek(s):
          return(s[len(s)-1])
      def isEmpty(s):
          return (s==[])
      def size(s):
          return(len(s))
          
contoh penggunaan fungsi-fungsi stacks yang telah dibuat:

    st=stack()
    isEmpty(st)
True

    push(st,100)
    push(st,23)
    push(st,34)
    pop(st)
    push(st,56)
    pop(st)
    print(st)
[100, 23]


 implementasi untuk penggunaan stacks ada 2, yaitu delimiter matching dan konversi desimal ke biner
 1.delimiter matching
   Parentheses sering digunakan untuk urutan penyelesaian dalam persamaan Matematika, seperti contoh berikut:
   P = 5 x (4 + 5) / ((3 + 2) x (10 - 8))
   secara umum  pemeriksaan parentheses ada 2, yaitu '{ }', '', dan '( )'
   
   sedangkan tahapan / algoritmanya bisa dilihat dibawah ini:
    a. Baca setiap karakter yang terdapat pada suatu string matematika
    b. Jika karakter adalah kurung buka, maka masukkan dalam stack
    c. Jika karakter adalah kurung tutup, ada beberapa kondisi yang harus diperiksa, yaitu :
    d. Jika stack dalam keadaan empty, maka jumlah kurung tutup lebih banyak daripada kurung buku
    e. Jika stack dalam keadaan tidak empty, maka maka pop stack, dan cocokkan karakter hasil pop dengan kurung tutup, jika sejenis,
       maka matched, jika tidak maka jenis kurung tidak sama
    f. Jika semua karakter telah terbaca, dan stack masih dalam keadaan terisi (tidak empty), maka jumlah kurung buka lebih banyak
       daripada kurung tutup
       
fungsi untuk pengecekan kurung pada suatu string matematika

      def stack():
          s=[]
          return (s)
      def push(s,data):
          s.append(data)
      def pop(s):
          data=s.pop()
          return(data)
      def peek(s):
          return(s[len(s)-1])
      def isEmpty(s):
          return (s==[])
      def size(s):
          return(len(s))
          
      def paranthesesCheck(strMath):
          operandStack=stack()
          lenMath=len(strMath)
          openOperand='({['
          closeOperand=')}]'
          #print(lenMath)
          i=0
          Matched=True;
          while i<(lenMath):
              #print(i,'=',strMath[i])
              if strMath[i] in openOperand:
                  push(operandStack,strMath[i])
                  #print(operandStack)
              elif strMath[i] in closeOperand:
                  if not (isEmpty(operandStack)):
                      top=pop(operandStack)
                      #print("top=",top)
                      #print (operandStack)
                      if openOperand.index(top)==closeOperand.index(strMath[i]):
                          Matched=Matched and True
                      else:
                          Matched=Matched and False
                          print ('Kurung Buka dan Kurang Tutup tidak Cocok')
                  else:
                      Matched=Matched and False
                      print('Jumlah Kurung Tutup lebih banyak')
              i=i+1
              #print(Matched)
          if not(isEmpty(operandStack)):
              Matched=False
              print('Jumlah Kurung Buka Lebih banyak')
          return(Matched)


Konversi Bilangan
adalah suatu proses dimana satu system bilangan dengan basis tertentu akan dijadikan bilangan dengan basis yang lain. 


Berikut algoritma untuk konversi ekspressi aritmatik infix ke postfix :
1. Buat struktur data stack untuk menampung operator
2. Baca ekspressi aritmatik dari kiri ke kanan tiap token :
      a. jika token yang dibaca adalah operand maka masukkan operand tersebut ke dalam output string
      b. jika token yang dibaca adalah kurung buka maka push kurung buka tersebut ke dalam stack
      c. jika token yang dibaca adalah kurang tutup maka pop stack semua token sampai ditemukan kurung buka
      d. jika token yang dibaca adalah operator maka :
            1. pop operator-operator yang memiliki precedence lebih tinggi atau sama dan masukkan operator tersebut ke dalam output                    string
            2. push token operator ke dalam stack
3. Jika masih terdapat operator pada stack, maka pop operator yang tersisa dan letakkan pada output string


Evaluasi Ekspressi Postfix
untuk ekspressi aritmatika Postfix dilakukan setelah terdapat dua buah operand sebelum sebuah operator.
Misalkan : 87+2*, yang berarti (8+7)*2=30,
oleh karena itu berikut algoritma untuk mengevaluasi ekspressi aritmatika postfix :
      1. baca string mulai dari kiri
      2. Jika character yang dibaca adalah sebuah operand, maka push operand tersebut.
      3. Jika character yang dibaca adalah sebuah operator, maka pop dua buah operand yang terdapat pada stack, operasikan dua buah           4. operand tersebut dengan operator, dan push hasil operasinya
      5. hasil akhir adalah angka terakhir yang terdapat di dalam stack


code untuk evaluasi ekspressi postfix

      def evaluatePost(postStr):
          operandStack=stack()
          operator='+-/*'
          for i in postStr:
              if i not in operator:
                  push(operandStack,i)
              else:
                  oprnd2=pop(operandStack)
                  oprnd1=pop(operandStack)
                  if i=='+':
                      result=float(oprnd1)+float(oprnd2)
                  elif i=='-':
                      result=float(oprnd1)-float(oprnd2)
                  elif i=='*':
                      result=float(oprnd1)*float(oprnd2)
                  else:
                      result=float(oprnd1)/float(oprnd2)
                  push(operandStack,result)
          return(pop(operandStack))

      print(evaluatePost('45-6*'))
-6.0


Tugas Soal Praktikum

Buatlah suatu modul dengan nama stack, dengan fungsi-fungsi utama yang terdapat dalam modul adalah:
- stack( ) : inisialisasi stack kosong
- push(data) : push suatu data ke dalam stack
- pop ( ) : penghapusan data yang berada pada top of the stack. Return value berupa data yang dihapus dari stack tersebut
- peep ( ) : informasi yang terdapat pada top of the stack
- isEmpty( ) : memeriksa stack apakah dalam keadaan kosong
- size( ) : informasi jumlah data yang terdapat pada stack

Buatlah modul dengan nama stackImplementation, yang berisi fungsi-fungsi untuk implementasi-implementasi penggunaan konsep stack, antara lain :
1. reverseWord (kata) :
Gunakan fungsi-fungsi yang terdapat pada modul stack untuk membalik suatu kata. Output dari fungsi reverseWord(kata) ini adalah kata yang sudah disusun secara terbalik, seperti berikut

            stack.reverseWord('kita')
            'atik'
      
2. decToBin(num) :
Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengkonversi suatu bilangan decimal menjadi bilangan biner, seperti contoh berikut :

            stack.decTobin(12)
            '1100'
      
3. evaluatePost(str):
Gunakan fungsi-fungsi yang terdapat pada modul stack untuk mengevaluasi ekspressi matematika postfix, dengan return value berupa hasil operasi matematika, dengan ketentuan sebagai berikut :
      a. antara operand maupun operator, dipisahkan dengan spasi,
         misalkan : 8 17 + yang berarti 8 + 17
      b. Tambahkan pengecekan error, antara lain :
            i. Jika jumlah operand terlalu banyak
            ii. Jika jumlah operand terlalu sedikit
            iii. Jika terdapat operasi pembagian dengan nol, seperti 9 0 /, yang berarti 9:0
Berikut adalah contoh penggunaan fungsi evaluatePost(str):

            a='6 0 81 *'
            evaluatePost(a)
      
'Error: Terlalu banyak operand'

            a='8 7 + 0 /'
            evaluatePost(a)
      
'Error: pembagian dengan nol'


            a='21 2 + */'
            evaluatePost(a)
      
'Error: operand terlalu sedikit'

            a='610 11 1 + - 5 *'
            evaluatePost(a)
      
-10.0

4. parenthesesCheck(str):
Gunakan fungsi-fungsi yang terdapat pada modul stack untuk pengecekan kurung pada ekspressi matematika, dengan return value berupa nilai True jika ekspressi matematika sudah benar, dan false jika masih terdapat kesalahan. Selain nilai True dan False, tambahkan pesan error jika terjadi kesalahan, antara lain :
      o Jumlah kurung buka terlalu banyak
      o Jumlah kurung tutup terlalu banyak
      o Kurung buka dan kurung tutup tidaklah cocok
Contoh penggunaan fungsi dan output yang dihasilkan, dapat dilihat pada contoh 

            parenthesesCheck('{(3+5)*(9-2)}')
(True, 'tidak ada eror')

            parenthesesCheck('(21/(56+2)')
(True, 'jumlah kurung buka lebih banyak')

            parenthesesCheck('(4-5)/12+7)')
(True, 'jumlah kurung tutup lebih banyak')

            parenthesesCheck('67*(5+2)/(12-6)')
(True, 'kurung buka dan kurung tutup tidak cocok')


Jawaban Praktikum

1. ReverseWord (kata)

            def cekPalindrome(kata):
                panjang_kata = len(kata)
                panjang_kata_array = panjang_kata - 1
                kata_dibalik = ''
                for p in range(panjang_kata):
                    kata_dibalik += kata[panjang_kata_array - p]
                print("{1}".format(kata, kata_dibalik))
            input_kata = input('Masukan sebuah kata: ')
            while True:    
                if input_kata is '':
                    print('Exit...')
                    break
                else:
                    cekPalindrome(input_kata.lower())
                    input_kata = ''
                    input_kata = input('\nCoba lagi kata baru (langsung ENTER untuk exit): ')


2. decToBin(num)

            def stack():
                s=[]
                return(s)
            def push(s,data):
                s.append(data)
            def pop(s):
                data=s.pop()
                return(data)
            def peek(s):
                return(s[len(s)-1])
            def IsEmpty(s):
                return(s==[])
            def size(s):
                return(len(s))
            def Biner(angka):
                s = stack()
                while angka > 0:
                    biner = int(angka%2)
                    push(s,biner)
                    angka = (angka-biner) / 2
                hasilBenar = ""
                for i in range(len(s)):
                    hasilBenar += (str(pop(s)))
                print("Hasil Biner:",end=" ")
                return (hasilBenar)
            print(Biner(12))
            
            
3. evaluatePost(str)

            import operasistack
            def evaluatePost(string):
                s=operasistack.stack()
                hasil = 0
                for i in string:
                    if i == '+':
                        if (operasistack.size(s)>2):
                            if (operasistack.peek(s)==' '):
                                operasistack.pop(s)
                            akhir=(operasistack.pop(s))
                            if operasistack.peek(s)==' ':
                                operasistack.pop(s)
                            hasil=operasistack.pop(s)+akhir
                            operasistack.push(s,hasil)
                        else:
                            return 'Error: operand terlalu sedikit'
                    elif i == '-':
                        if (operasistack.size(s)>2):
                            if (operasistack.peek(s)==' '):
                                operasistack.pop(s)
                            akhir=(operasistack.pop(s))
                            if operasistack.peek(s)==' ':
                                operasistack.pop(s)
                            hasil=operasistack.pop(s)-akhir
                            operasistack.push(s,hasil)
                        else:
                            return 'Error: operand terlalu sedikit'
                    elif i == '*':
                        if (operasistack.size(s)>2):
                            if (operasistack.peek(s)==' '):
                                operasistack.pop(s)
                            akhir=(operasistack.pop(s))
                            if operasistack.peek(s)==' ':
                                operasistack.pop(s)
                            hasil=akhir*operasistack.pop(s)
                            operasistack.push(s,hasil)
                        else:
                            return 'Error: operand terlalu sedikit'
                    elif i == '/':
                        if (operasistack.size(s)>2):
                            if (operasistack.peek(s)==' '):
                                operasistack.pop(s)
                            akhir=(operasistack.pop(s))
                            if operasistack.peek(s)==0:
                                return 'Error : Pembagian dengan nol'
                            akhir=(operasistack.pop(s))
                            if operasistack.peek(s)==' ':
                                operasistack.pop(s)
                            hasil=operasistack.pop(s)/akhir
                            operasistack.push(s,hasil)
                        else:
                            return 'Error: operand terlalu sedikit'
                    elif i==' ':
                        operasistack.push(s,i)
                    else:
                        if not(operasistack.isEmpty(s)):
                            if (operasistack.peek(s)!=' '):
                                jumlah=(operasistack.pop(s)*10) + int(i)
                                operasistack.push(s,jumlah)
                            else:
                                operasistack.push(s,int(i))
                        else:
                            operasistack.push(s,int(i))
                if operasistack.size(s)>1:
                    return 'Error: operand terlalu sedikit'
                else:
                    return operasistack.pop(s)
                    
4. parenthesesCheck(str)

            import operasistack
            def parenthesesCheck(string):
                s=operasistack.stack()
                for i in string:
                    if i == '(':
                        operasistack.push(s,i)
                    if i ==')':
                        if operasistack.isEmpty(s):
                            return False,'kurung tutup lebih'
                        else:
                            operasistack.pop(s)
                    if i == '{':
                        operasistack.push(s,i)
                    if i == '}':
                        if operasistack.isEmpty(s):
                            return False
                        else:
                            operasistack.pop(s)
                if operasistack.isEmpty(s):
                    return True, 'Tidak ada error'
                else:
                    return False, 'Kurung Buka lebih'
