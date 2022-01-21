# Exercise 6 - Mapping and Understanding Attack Surface

The goal of this exercise is to get us to think about how we might execute an attack against an ECU. In this exercise we are going to make use of the SPC560P-Disp Development Board. On SPC560P-Disp Development Board we are going to execute a LIN BUS receive/transmit program.

* [LIN Bus Transmit/Receive SPC5 Studio Project](https://github.com/Merimetso-Code/EmbeddedAutomotiveSecurity/blob/main/EXERCISE6.zip)
* [SPC560P-Disp Development Board](2520506-40.jpg)

For the LIN bus receive project we should have the following:
```c
static uint16_t lin_master_receive(LinDriver *ldp, uint8_t idMessage, uint8_t *buffer, uint16_t msg_len) {
  volatile struct spc5_linflexl *linflexlp = ldp->linflexlp;

  if ((msg_len == 0U) || (msg_len > 8U)) {
    return 0;
  }

  SPC5_LIN_RX_IN_PROGRESS(ldp);

  /* Prepare buffer for receiving data */
  ldp->rx_buf = buffer;
  ldp->rx_len = msg_len;

  /* Prepare message header */
  linflexlp->BIDR.R = 0;
  linflexlp->BIDR.B.ID  = idMessage & SPC5_BIDR_ID_MASK;
  linflexlp->BIDR.B.DFL = (uint8_t)(((uint32_t)msg_len - 1U) & SPC5_BIDR_DFL_MASK); /* Configure DFL in BIDR */
  linflexlp->BIDR.B.CCS = 0;
  linflexlp->BIDR.B.DIR = (uint8_t)LIN_DIRECTION_RECEIVE;

  /* Enable Data Receive interrupt */
  linflexlp->LINIER.B.DRIE = 1;

  /* Trigger Header transmission*/
  linflexlp->LINCR2.B.HTRQ = 1;

  SPC5_LIN_WAIT_FOR_RX_COMPLETION(ldp);

  /* rx_len could have been changed at interrupt time */
  return ldp->rx_len;
}
```

And for the LIN bus transmit project we should have the following
```c
static void lin_master_transmit(LinDriver *ldp, uint8_t idMessage, uint8_t *buffer, uint16_t msg_len) {
  volatile struct spc5_linflexl *linflexlp = ldp->linflexlp;

  if ((msg_len == 0U) || (msg_len > 8U)) {
	  return;
  }

  SPC5_LIN_TX_IN_PROGRESS(ldp);

  /* Save message parameters */
  ldp->tx_id_msg = idMessage;
  ldp->tx_buf = buffer;
  ldp->tx_len = msg_len;

  /* Set Header */
  linflexlp->BIDR.R = 0;
  linflexlp->BIDR.B.ID = idMessage & SPC5_BIDR_ID_MASK;
  linflexlp->BIDR.B.DFL = (uint8_t)(((uint32_t)msg_len - 1U) & SPC5_BIDR_DFL_MASK); /* Configure DFL in BIDR */
  linflexlp->BIDR.B.CCS = 0;
  linflexlp->BIDR.B.DIR = (uint8_t)LIN_DIRECTION_TRANSMIT;

  /* Check if DMA is enabled.*/
#if (SPC5_LIN_DMA_MODE == SPC5_LIN_DMA_ON)
  /* Check if the LinFlex support DMA.*/
  if ((ldp->dma_supported == TRUE) && (ldp->config->dma_enable == TRUE)) {
    ld_txi_dma(ldp, buffer, msg_len);
  } else {
    ld_txi(ldp, buffer, msg_len);
  }
#else
  ld_txi(ldp, buffer, msg_len);
#endif /* (SPC5_LIN_DMA_MODE == SPC5_LIN_DMA_ON) */

  /* Enable transmit interrupt */
  linflexlp->LINIER.B.DTIE = 1;

  /* Trigger Header transmission*/
  linflexlp->LINCR2.B.HTRQ = 1;

  SPC5_LIN_WAIT_FOR_TX_COMPLETION(ldp);
}
```

Once you have programmed the SPC560P board so that it are executing the required software you can now examine the system from a holistic perspective for vulnerabilities. In particular, we examining the attack surface for a system you should ask the following questions:

* Does the hardware contain any
    * data access ports such as USB, CAN, LIN and Ethernet and are these data ports used.
    * debug/programming ports such as I2C, SPI and JTAG and how can these ports be accessed.
* Does the software contain any vulnerabilities, such as
    * Can I write more that 8 bights of data to the CAN bus
    * I am using vulnerability functions such as strcpy()
    * Can I modify the data that is being transmitted over the CAN bus

## Advanced Topics

If you have an oscilloscope or a logic analyse then you may wish to mount a man in the middle attack and observe and analyses the data in the LIN Bus. Questions that you might like to answer are:

* What is the data that is being transmitted over the CAN bus?
* At what speed is the data being transmitted?

# Tips and Hints
Information and help on programming in C can be found on the following links:
* [Programming in C](https://beginnersbook.com/2014/01/c-program-structure/)
* [A C Tutorial](https://www.cprogramming.com/tutorial/c-tutorial.html?inl=nv)
* [Loops in C](https://www.tutorialspoint.com/cprogramming/c_loops.htm)

## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. <ablyth@merimetso.net>
