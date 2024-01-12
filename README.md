/ *
  
   * Haga clic en nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt para cambiar esta licencia
   * Haga clic en nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java para editar esta plantilla
   * /
   paquete Tecladogabrielacevallos;

  importar javax.swing. * ;
  importar java.awt. * ;
  importar java.awt.event.ActionEvent;
  importar java.awt.event.KeyEvent;
  importar java.awt.event.KeyListener;
  importar java.util.Arrays;
  importar java.util.List;

  clase pública TecladoGabrielaCevallos extiende JFrame {
      área de texto JTextArea final privada;
      Lista final privada< String > pangramas;

      público TecladoGabrielaCevallos() {
          super("TecladoGabrielaCevallos ");
          setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
          setLayout(nuevo BorderLayout());

          área de texto = nueva JTextArea();
          textArea.setEditable(verdadero);
          textArea.setLineWrap (verdadero);
          textArea.setWrapStyleWord (verdadero);

          JScrollPane scrollPane = nuevo JScrollPane(textArea);
          agregar(scrollPane, BorderLayout.CENTER);

          pangramas = Arrays.asList(
              "El veloz murciélago hindú comía feliz cardillo y kiwi.",
              "Joven exquísito, ahorra papeles blancos, dirigiéndose vueltas zigzagueantes.",
              "Mi hacha cymban con fluído xilofón de ébano.",
              "Un pingüino jugando vóley brilló más que los demás.",
              "El jefe del cementerio silbó canciones y lo hizo feliz",
              "Zambrulló el whisky rígido, y poco fue su escape.",
              "Felpudo juerguista, ¡qué bien bailas, xilófono!",
              "Cómo vacío su jarra de whisky el caníbal.",
              "Jovencillo emponzoñado de whisky, ¡qué figurota exhibes!",
              "El oso yogui en su taxi fue por whisky.",
              "Juan, rápido, cómprame un taxi volador de juguete.",
              "Mi tía Beatriz va examinando su buzón de joyas, flores y vítores.",
              "El führer jugaba al ajedrez y empezó a vencer.",
              "Vexilología, estudio de las banderas, me fascina.",
              "La cigüeña toca jazz con el saxofón y el bongo.",
              "Quizás el único que con whisky no ha estado es mi jefe.",
              "La abuela apreció su pastel de kiwi y fresa.",
              "Juanito hizo que el muy bravo boxeador se fuera",
              "La jirafa toca el xilófono bajo el cielo nublado.",
              "¿Quién compró tres kilos de yuca para el jabalí?",
              "¿Quién compró tres kilos de yuca para el jabalí?"
          );

          Panel de teclado JPanel = createKeyboardPanel();
          agregar (panel de teclado, BorderLayout.SUR);

          setFocusable(verdadero);
          establecerTamaño(800, 400);
          setLocationRelativeTo(nulo);
          setVisible(verdadero);

          textArea.requestFocusInWindow();
          addKeyListener(nuevo CustomKeyListener());
      }

      JPanel privado createKeyboardPanel() {
          Panel de teclado JPanel = nuevo JPanel (nuevo GridLayout (4, 10, 5, 5));
          Cadena [] etiquetas clave = {
              "1", "2", "3", "4", "5", "6", "7", "8", "9", "0",
              "Q", "W", "E", "R", "T", "Y", "U", "I", "O", "P",
              "A", "S", "D", "F", "G", "H", "J", "K", "L", "Ñ",
              "Z", "X", "C", "V", "B", "N", "M", " ", "⌫"
          };

          para (String keyLabel: keyLabels) {
              JButton keyButton = nuevo JButton(keyLabel);
              keyButton.addActionListener(this::handleKeyButtonClick);
              tecladoPanel.add(keyButton);
          }

          devolver tecladoPanel;
      }

      handleKeyButtonClick vacío privado (ActionEvent e) {
          Comando de cadena = e.getActionCommand();

          si (comando.equals ("⌫")) {
              Cadena texto actual = textArea.getText();
              si (!currentText.isEmpty()) {
                  textArea.setText(currentText.substring(0, currentText.length() - 1));
              }
          } demás {
              textArea.append(comando);
          }
      }

      clase privada CustomKeyListener implementa KeyListener {
          @Anular
          clave pública vacía Typed (KeyEvent e) {
              char keyChar = e.getKeyChar();
              textArea.append(String.valueOf(keyChar));


              Cadena currentInput = textArea.getText().toLowerCase();
              for (String pangrama : pangramas) {
                  if (pangrama.toLowerCase().startsWith(currentInput)) {
                      textArea.append("\n[Sugerencia]: " + pangrama.substring(currentInput.length()));
                      romper;
                  }
              }
          }

          @Anular
          tecla pública vacía presionada (Evento clave e) {

          }

          @Anular
          clave pública vacíaReleased(KeyEvent e) {

          }
      }

      público estático vacío principal (String [] argumentos) {
          SwingUtilities.invokeLater(TecladoGabrielaCevallos::new);
      }
  }
