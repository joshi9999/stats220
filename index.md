library(magick)

normal_pooh <- image_read("https://uploads.dailydot.com/2019/04/apathetic_winnie-the_pooh.gif?auto=compress&fm=gif&ixlib=php-3.3.0"
) %>%
image_scale(500)
tuxedo_pooh <- image_read("https://uploads.dailydot.com/2019/04/tuxedo_winnie_the_pooh.jpg?auto=compress&fm=pjpg&ixlib=php-3.3.0") %>%
image_scale(500)
monocle_pooh <- image_read("https://cdn.drawception.com/drawings/2zLQXLyKZm.png") %>%
image_scale(500)
early <- image_blank(width = 1000,
height = 500,
color = "#C33618") %>%
                         image_annotate(text = "Easily do 220 assignment the day it is released and seek help early during lab sessions",
                                        color = "#2456E4",
                                        size = 24,
                                        font = "Comic_Sans",
                                        gravity = "center")
                         middle <- image_blank(width = 1000,
                                                  height = 500,
                                                  color = "#C33618") %>%
                           image_annotate(text = "Attempt 220 assignment the weekend before due date and spam question on Ed",
                                          color = "#2456E4",
                                          size = 24,
                                          font = "Comic_Sans",
                                          gravity = "center")
                         late <- image_blank(width = 1000,
                                                height = 500,
                                                color = "#C33618") %>%
                           image_annotate(text = "Start 220 assignment 2 hours due date, realize you don't know anything and beg for extension",
                                          color = "#2456E4",
                                          size = 21,
                                          font = "Comic_Sans",
                                          gravity = "center")
                         first_row <- c(normal_pooh, early) %>%
                           image_append()
                         second_row <- c(tuxedo_pooh, middle) %>%
                           image_append()
                         third_row <- c(monocle_pooh, late) %>%
                           image_append()
pooh_meme <- c(first_row, second_row, third_row) %>%
              image_append(stack = TRUE)
  
image_write(pooh_meme, "pooh_meme.png")
