#!/usr/bin/python

class Queue:
  def __init__(self):
      self.items = []
  
  def __str__(self):
      values = [str(x) for x in self.items]
      return ' '.join(values)

  def isEmpty(self):
    if self.items == []
      retrun True
