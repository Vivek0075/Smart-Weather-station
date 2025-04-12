#include "main.h"
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
int main(void)
{  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
 while (1)
 { // Turn on the LED
  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
 HAL_Delay(500); // Delay 500ms
// Turn off the LED
HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
 HAL_Delay(500); // Delay 500ms  }}
void SystemClock_Config(void)
{ RCC_OscInitTypeDef RCC_OscInitStruct = {0};
 RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
 HAL_RCC_PWR_CLK_ENABLE();
HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE1);
RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSI;
RCC_OscInitStruct.HSIState = RCC_HSI_ON;
RCC_OscInitStruct.HSICalibrationValue = RCC_HSICALIBRATION_DEFAULT;
RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
 {Error_Handler();}
RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK | RCC_CLOCKTYPE_SYSCLK | RCC_CLOCKTYPE_PCLK1 | RCC_CLOCKTYPE_PCLK2;
RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_HSI;
RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
 RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;
 if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
 { Error_Handler();}}
static void 
MX_GPIO_Init(void)
{GPIO_InitTypeDef GPIO_InitStruct = {0};
/* GPIO Ports Clock Enable /
 __HAL_RCC_GPIOA_CLK_ENABLE();
 /Configure GPIO pin Output Level /
 HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
 /Configure GPIO pin : PA5 */
GPIO_InitStruct.Pin = GPIO_PIN_5;
GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
 GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
 HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
}


![image](https://github.com/user-attachments/assets/988ada70-e5f4-4d2c-b498-88c07208a759)



  
![image](https://github.com/user-attachments/assets/335a3486-2daa-4c54-baf9-6ed4f33252bf)

   
![image](https://github.com/user-attachments/assets/dc8184db-68a5-4781-b6c5-d67eefaea700)
