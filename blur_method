class Image
  attr_accessor :targets, :rows, :distance

  def initialize(image)
    @rows = image
    @targets = []

    # loop through rows
    @rows.each_with_index do |cells, row_index|
      # loop through cells
      cells.each_with_index do |cell, cell_index|
        # find cells that are 1
        if cell == 1
          # create hash with row/cell as key and index as value
          @targets << {target_row: row_index, target_cell: cell_index}
        end
      end
    end
  end

  def blur(distance)
    @distance = distance.to_i

    final_array = @rows

    @rows.each_with_index.map do |cells, row_index|
      cells.each_with_index.map do |cell, cell_index|
        #run through each of the targets and compare their locations to current location
        @targets.each do |target|
          row_index_difference = target[:target_row] - row_index
          cell_index_difference = target[:target_cell] - cell_index
          neg_dist = @distance * -1

          case row_index_difference
            when (neg_dist..-1)
              if cell_index_difference == 0
                final_array[row_index][cell_index] = 1
              elsif (cell_index >= target[:target_cell] - @distance - row_index_difference) && (cell_index <= target[:target_cell] + @distance + row_index_difference)
                final_array[row_index][cell_index] = 1
              end
            when 0
              if cell_index_difference <= @distance && cell_index_difference >= neg_dist
                final_array[row_index][cell_index] = 1
              end
            when (1..@distance)
              if cell_index_difference == 0
                final_array[row_index][cell_index] = 1
              elsif (cell_index >= target[:target_cell] - @distance + row_index_difference) && (cell_index <= target[:target_cell] + @distance - row_index_difference)
                final_array[row_index][cell_index] = 1
              end
          end
        end
      end
    end
    
    final_array.each do |element|
      puts element.join("")
    end
  end
end

image = Image.new([
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
])

image.blur(4)


